---
title: Project
index: 5000
icon: project
---

A *Project* is the most common Clarive security [Scope](/concepts/scope).

A Clarive Project is a collection of [Topics](/concepts/topic), and is defined according to your organization's
requirements. For example, a Clarive Project could be:

- A software development project.
- A system.
- A group of software components.
- (More commonly) an application.

Topics can belong to zero, one or more Projects, but that is not a requirement.  For example, Changeset Topics must
belong to one (and only one) Project.

Releases, on the other hand, may be multi-project or have no Projects.

## Project Variables

Every Project can have a set of variables with values set specifically for that Project. Moreover, for every
[Environment](/concepts/environment), different values can be set.

Variables may be configured in an [Project Template](/how-to/project-template)according to the Environment(s) in
which they are available or are assigned a given value. These variables are referenced in Projects in a similar way to
when referencing simple variables, with the difference that their values are then imported by selecting from the *Import
Configuration* combo the Environment Template in which these were configured.

### Copying variables between Environments

Setting variables can be a cumbersome process, and it is very common for different Environments to have the same
variables, albeit with different values. That is where copying vars to another environment can be a real help. If the
[variable](/concepts/variable) has a Copy flag it is copied with the current value.

### Nature variables

Nature variables are built from selected natures and their blueprints.
