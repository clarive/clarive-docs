---
title: Artifact Repository Manager
index: 5000
icon: artifacts
---

Clarive has an integrated artifact repository manager that is capable of managing the delivery of artifacts (or
components) to build tools such as Maven or similar.

The key features of the Clarive artifact manager are:

- server repository of any kind of files (or artifacts), from binary executables to packaged libraries and metadata.
- files published are accessible through HTTP(S) navigation.
- a in-tool artifact browser with search and tagging.
- remote repository proxying.
- database artifact indexing a storage.
- access-control to artifacts and directories.
- repository groups.

The Clarive artifact repository management system is controlled by a set of three Resources:

- Local Artifact Repository (ArtifactLocal).
- Remote Artifact Repository (ArtifactRemote).
- Repository Group (ArtifactGroup).

Repository management in Clarive is uncomplicated, unlike other tools on the market. A local repository points to
a location in the filesystem (or database) that contains a structure of artifacts.  A remote repository points to a URL
that can provide a given artifact. A group is an ordered set of both local and remote artifacts.

To create your first repository, start by creating a Resource
 of type __Local Artifact Repository__. Read below for details.

## Root URL

All repositories served by Clarive start from the base url `/artifacts/repo`:

    http(s)://[clarive-server:port]/artifacts/repo/[url-prefix]

## Local Artifact Repository (ArtifactLocal)

A Clarive local artifact repository is a filesystem location where artifacts are stored and made accessible through
a URL path.

The ArtifactLocal Resource
 represents a location in the filesystem that holds a directory structure of artifacts, with
a corresponding URL prefix.

For example, for a Local Repository Resource
 called "MyRepo" you may
want to define a local directory for storing the files at
the following location:

    /opt/repositories/myrepo

and a URL prefix of:

    myrepo

The URL base for this repository would be:

    http(s)://[clarive-server:port]/artifacts/repo/myrepo

### Creating a Local Artifact Repository Resource


The minimum requirement for creating a local repository is to set a Resource
 `Name`, define a `URL Prefix` and a `Local Path to
Repository`.

- **Name** - the name does not influence any of the URL or directory related operations.
- **URL Prefix** - this is the URL path part after `/artifacts/repo` where repositories and their files will be
  accessible to users, scripts and build systems that depend on it.
- **Local Path to Repository** - the physical location of the artifact repository in the server filesystem, also called
  a _root path_.  If the local path does not exist, it will be created by Clarive.

#### Local Path Auto-Selection

If no local path is defined, upon saving the Resource, Clarive will set the path to a combination of the global config
variable `config.artifacts.path` and the URL prefix.

After saving, reload the Resource
 to see the new value.

#### Access Mode: Public

Local repositories with **Public** access mode can be navigated through the interface and the artifacts it contains can
be downloaded by any user that has the URL.

#### Access Mode: Hidden

By default, local repositories are public.  But in **Locked** mode, the repositories are not accessible by anyone, except
through a repository group.

Locked mode is therefore ideal for defining local storage locations that can later be combined into a repository group.

### Exact Matching Mode

By default, local repository files are matched exactly to the requested filename.

To perform near matches, use the **Prefix** mode.

### Prefix Matching Mode, White and Blacklisting

In the **Prefix** matching mode, files served by a local directory do not need to be exact. Clarive will attempt to
match all possible files that **start** with the filename requested.  A local artifact repository may also have
white/blacklisted artifacts that allow for administrators to better control what types of files are returned by Clarive.

To understand how white/blacklisting works, first we need to make the distinction between the two types of input lists:

- files - a filename requested by the user, build tool etc.
- images - a file found by Clarive in the filesystem.

If more than one image matches for a given file request, the first image matched is returned.

Example:

    Requested file:

    http://clarive/artifacts/repo/myrepo/file.jar

    Matching images:

    http://clarive/artifacts/repo/myrepo/file_v01.jar
    http://clarive/artifacts/repo/myrepo/file_v00.jar

    File served:

    http://clarive/artifacts/repo/myrepo/file_v01.jar

#### Regular expression

All lists are regular expressions, so they need to be written with separating `|` (pipes).

#### Whitelisted Files

A list of file patterns that can be requested by the user or build tool. Patterns can match any part of the file name or
requested URL.

An empty file whitelist means ANY file pattern can be requested. If the file does not match the pattern, it is discarded
immediately.

#### Blacklisted Files

A list of file **suffixes** that cannot be requested by the user or build tool.

An empty blacklist of files means NONE is blacklisted.

**Note**: even if a file is blacklisted, it may be served due to an image whitelist. See below.

Example:

    Requested file:

    http://clarive/artifacts/repo/myrepo/file.jar

    Blacklisted files:

    -source|-sources

    Matching images:

    http://clarive/artifacts/repo/myrepo/file.jar
    http://clarive/artifacts/repo/myrepo/file-sources.jar

    File served, which excludes the blacklisted files:

    http://clarive/artifacts/repo/myrepo/file.jar

#### Whitelisted Images

Images are files found in the artifact repository that match the filename detected.

The whitelisted image pattern will match any part of the path or file name requested.

**Important**: even if a file is blacklisted, if there are any matching whitelisted images, the images will be served
back to the requestor by Clarive. However, only whitelisted images that have the requested filename will be returned.

#### Blacklisted Images

Images are files found in the artifact repository that match the filename detected.

## Remote Artifact Repository (ArtifactRemote)

A remote artifact repository is a URL location from where Clarive can download artifacts and serve them to the user.

Remote artifact repositories allows Clarive to act as a proxy between the user and the remote artifact.

### Creating a Remote Artifact Repository

To create a remote artifact repository, you need only the Resource
 `Name` and `URL to Remote Repository` fields.

- **Name** - the name is just the Resource
 name and does not impact on how the repository is used or accessed remotely.
- **URL to Remote Repository** - a URL to an artifact repository that can deliver the files requested. Typically this
  URL will be served over the internet, although it could also point to other repositories within the intranet or private cloud of an
  organization.

#### Remote to Local Association

In order to enable a remote repository for use, first it is necessary to have a local repository that bridges to the
remote one.

Having a local-remote repository association creates a locally cached remote repository. That way, files that are
frequently requested by builds will be cached locally (in a server directory), and may be indexed, searched and traversed by
users.

## Repository Group (ArtifactGroup)

A repository group is an **ordered** set of local repositories that are logically bundled into one URL prefix.

Why use repository groups?

1. to have local repositories organized in different ways and locations without impacting users and builds that can
   break with a URL prefix reorg.
2. to have a set of **failback** repositories that allow the user or build system to try several locations before
   finally returning a 404 (not found) code.

We recommend the use of repository groups, precisely for these reasons.  Groups are a single entry point for users
to the artifact repository hierarchy.

### URL mapping from group to local

URL prefixes of local repositories will be replaced by the group prefix when a local repository is accessed through
a group.

For example, suppose we have the following local repository:

    url_prefix: mylocal

and normally, within the local repository, we can access the following file:

    http://clariveserver/artifacts/repo/mylocal/dir1/file1.jar

and the following is a group prefix for a group that contains the above local repository:

    url_prefix: mygroup

Then the following URL will also be made available to users:

    http://clariveserver/artifacts/repo/mygroup/dir1/file1.jar

effectively replacing the previous `mylocal/` URL path part with the new one.

## Repository Error Messages

The repositories may generate the following errors and error messages:

#### 400 Bad Request

This error message means that the repository prefix does not exist in the Clarive repository management system.

Here is an example in Maven:

    [ERROR] Plugin org.apache.maven.plugins:maven-clean-plugin:2.5 or one of its
    dependencies could not be resolved: Failed to read artifact descriptor for
    org.apache.maven.plugins:maven-clean-plugin:jar:2.5: Could not transfer
    artifact org.apache.maven.plugins:maven-clean-plugin:pom:2.5 from/to central
    (http://clarive:8080/artifacts/repo/local): Failed to transfer file:
    http://clarive:8080/artifacts/repo/local/org/apache/maven/plugins/maven-clean-plugin/2.5/maven-clean-plugin-2.5.pom.
    Return code is: 400, ReasonPhrase:Bad Request. -> [Help 1]

Check your URL prefix, which is the part that comes right after the `/artifacts/repo/` part.

#### 404 File Not Found

This error indicates that an artifact was not found in the repository, but the repository itself exists.

In Maven, the error could look somewhat like this. Notice that the error code is not visible here:

    [ERROR] Failed to execute goal on project my-app: Could not resolve
    dependencies for project com.mycompany.app:my-app:jar:1: Failed to collect
    dependencies at com.dbcx.core:dropbox-core-sdk:jar:LATEST: Failed to read
    artifact descriptor for com.dbcx.core:dropbox-core-sdk:jar:LATEST: Failed
    to resolve version for com.dbcx.core:dropbox-core-sdk:jar:LATEST: Could
    not find metadata com.dbcx.core:dropbox-core-sdk/maven-metadata.xml in
    local (/opt/mavenprj/.m2/repository) -> [Help 1]

The 404 error could be caused either by a misconfiguration in the user's or process build/packaging script, or by the
fact that the organization has decided not to make the file available to the user through blacklisting.

# Using the Clarive Artifact Repository with Package Managers

The Clarive artifact repository management system can be used together with many different package management systems,
not just build systems like Maven.

Private repositories is an ideal method for publishing and controlling the versions of packages used within an
organization.

Below are some examples of using Clarive with many popular package managers.

### Node NPM

The NodeJS NPM package manager uses the concept of a `registry`, which is a URL that contains a NPM repository.

To have Clarive proxy an NPM registry, first create a remote that points to a public Node registry, such as (the
official public Node registry):

    Remote URL: https://registry.npmjs.org/

Then create a local repository to cache the artifacts downloaded and connect it to the remote.

Once the Clarive Resources are created, you can set the npm registry on the command-line. Suppose you set the URL prefix to
`local-npm`, you can now install Node JS packages through Clarive:

    npm install --registry http://clarive:8080/artifacts/repo/local-npm babel

or simply configure the registry in your `$HOME/.npmrc` file that points to the Clarive NPM repository you just created:

    ; pointing the local NPM repository in Clarive
    registry = http://clarive:8080/artifacts/repo/local-npm

### Python PyPI

The Python PyPI package management system can use Clarive to proxy and control packages downloaded.

First create a remote artifact Resource
 that points to the remote URL of a Python PyPI repository:

    Remote URL: http://pypi.python.org/simple/

then create a local repository to cache the artifacts downloaded and connect it to the remote.

Now simply set the URL of the Clarive artifact manager url-prefix using the `--index-url` (or `-i`) of Python's
`easy_install`.

    easy_install -i http://clarive:8080/artifacts/repo/pypi/ [package_name]

### Perl and CPAN

Using Clarive with CPAN package managers is simple, just create a remote that points to one of many CPAN mirrors around
the internet. For example:

    Remote URL: https://cpan.metacpan.org

and create the local Resource with a URL prefix `cpan` and add the remote Resource to the Remote Repositories field.

Now you can install Perl packages proxying through Clarive.

    cpanm --mirror-only --mirror http://clarive/artifacts/repo/cpan Moose
