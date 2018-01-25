---
title: Docker
index: 890
---

Clarive rulebooks require Docker installed to run OS shell commands.

Docker is a great companion to your DevOps stack:

1. Docker containers allow your project and repository rulebooks to run pipelines
alongside any __necessary infrastructure__ without requiring additional software packages
to be installed in the Clarive server.

2. __Isolate__ your users from the server environment, so that
they cannot break anything.

3. __Version__ your infrastructure packages, so that different versions
of an app can run different versions of an image.

4. __Simplify__ your DevOps stack by having most of your build-test-deploy
continuous delivery workflows to run in one server (or more, if you have a cluster of Clarive servers),
instead of having to install runners for every project everywhere.

<img src="/static/images/docs/rulebook/docker-overview.png" style="width: 100%; height: 100%" />

## The default Docker container image

When you run a `shell:` op or one of [its variations](/rulebook/shell-commands),
Clarive will run the shell command in a Docker container.

If you don't specify the image name, Clarive will `docker pull`
a Docker image from the Docker Hub called `clarive/rulebook-runner`
which is [available here](https://hub.docker.com/r/clarive/rulebook-runner/).

## Specifying the `image:`

The `image:` rulebook op configures which Docker container image
will be used by Clarive to run commands.

```yaml
# sets the python image as the default to entire rulebook

image: python
do:
   - python --version  # this will run in the python container
```

You can also switch images inline.

```yaml
do:
   - image: python
   - python --version  # this will run in the python container
```

When you use an __image for the first time__, it may take from a few seconds to
a few minutes (depending on your internet connection) for Clarive to `docker
pull` and `docker build` the version of your image that will be used in your
rulebook.

## How do shell commands run

Every shell command in a rulebook runs within `bash` with a `docker run`
command.

This is important as it means the container starts and ends with every command.

If you need to run a stable sequence of commands, just execute them
as a single command:

```yaml
do:
    - image: python
    - |
         echo "print(123)" > /clarive/my.py
         python /clarive/my.py
         cd /tmp/
         ls -lart
```

## Available volumes

Volumes are the directories mapped from host to container guest
using the `docker run -v` command-line option.

Every container session has the following directory structure
available as individual volumes:

     /clarive/
     /clarive/.public     # files shared amongst all projects
     /clarive/.artifacts  # files here are loaded into the Clarive artifact repository

If you use the `workspace:` op to clone git repositories from your projects,
there will be additional folders mapped inside. For instance:

      /clarive/myproject/myrepo

## Setting the container user

Every shell command sent is run using the default `clarive` user.

To run commands with a different user, pass the `user:` parameter
to the `image:` op.

```yaml
image:
  name: python
  user: root
do:
  - whoami     # root
```

The user is sent with the `docker run -u|--user` command line option.
This option takes the argument as such: `user|uid[:group:gid]`.

```yaml
image:
  name: python
  user: "0:0"   # this works too
do:
  - whoami     # root again
```

Or set a different user for every command and container:

```yaml
do:
  - image:
      name: python
      user: root
      do:
         - whoami

  - image:
      name: ruby
      user: rubyuser
      do:
         - whoami
```

### Setting the container image version

You can set the container image version in the name:

```yaml
do:
   - image: "python:latest"   # latest is actually the default
   - python --version
   - image: "ruby:1.7.2"
```

### Setting container environment variables

You can send environment variables to the container.

```yaml
image:
  name: python
  environment:
      MY_DIR: "/tmp"
do:
   - ls -lart $MY_DIR

   # or, if you want to use the ${} notation in a bash shell
   # you need to escape it with double dollar `$${}`

   - ls -lart $${MY_DIR}
```

Or for a more evolved example using serverless and AWS, using variables defined
using the Variables admin UI:

```yaml
image:
  name: laardee/serverless
  environment:
      AWS_ACCESS_KEY_ID: "{{ ctx.var('aws_key') }}"
      AWS_SECRET_ACCESS_KEY: "{{ ctx.var('aws_secret') }}"
do:
   - serverless deploy
```

## The default Dockerfile

Clarive does not use the Docker image you set in `image:` as is.

After downloading the container image from the Docker Hub, Clarive runs `docker build`
to create a new version of the image with a clarive-specific `Dockerfile`.

    ARG image_name
    FROM $image_name
    ARG UID
    RUN useradd -ms /bin/bash -u $UID clarive ; exit 0
    RUN adduser -s /bin/bash -u $UID clarive ; exit 0

    USER clarive
    ARG workspace_dir
    WORKDIR $workspace_dir

This is so that we always run Clarive with the same user within that image.

Images that are built using this `Dockerfile` are renamed `clarive/imagename...`.

If you absolutely _must_ modify the Clarive standard Dockerfile for your taste, add the
following keys to your `CLARIVE_BASE/config/yourconfig.yml`:

```yaml
docker:
    dockerfile: "path/to/your/dockerfile_folder/"  # <--- Dockerfile must reside in this folder
```

!!! note
    You can only modify the Dockerfile in the on-prem Clarive version.
    The cloud version is restricted to the standard `Dockerfile`.

## Running commands on other servers

Clarive uses Docker for running shell commands __locally__.

But you can still run shell commands in other servers and systems,
such as Linux, Windows, various Unixes flavors and other legacy
systems (including the mainframe!) using the `host:` option in
the `shell:` command.

```yaml
deploy:
    - shell:
         cmd: `service mariadb restart`
         host: "dbserver1"
```

This will run a command in that server using either a predefined
node resource connection or with a clax agent/worker.

To setup a node, use the Resources admin UI interface.

## How do I use my own containers

If the container is not available on the Clarive server,
the Clarive rulebook downloads the container from Docker Hub.

So, to use your own containers, you have 2 options:

1. upload them to Docker Hub. Then use them from your rulebook.
Clarive will download it on the first run.

2. [__on-premise only__] install it in your Clarive server.
On the first run Clarive will build another version of your container
based on Clarive's default `Dockerfile`, called `clarive/yourcontainer`.
You don't need to prefix `clarive/` into the name, that's done for you automatically.

!!! tip "Roadmap"
    We'll soon be releasing a built-in container registry
    in Clarive. So stay tuned!
