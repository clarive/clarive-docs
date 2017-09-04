---
title: Environment
index: 5000
icon: ci-bl
---

In DevOps, an *environment* typically is defined as a place into which we deploy changes. To be more precise, we may
think of an environment as a logical grouping of [Resources](/concepts/resource).

### Environment Resource

In Clarive, an environment is itself a **Resource**. By creating a new Resource you are creating an environment.

### How do I configure the contents of an environment?

This is mostly done in one of two ways:

- For each Resource we create, we can set the environment to which it belongs. Some Resources do not support this, such
  as the Project Resource, whilst others such as the GenericServer do.
- For every [scope](/concepts/scope) or [project](/concepts/project), we can define which Resources belong to a given
  environment for that particular scope.

### Environment Naming

*DEV, TEST, QA, PRE, PREP* (preproduction), *PRO* and *PROD* (production) are all names of environments often used. By
convention, we propose environment names be limited to two to four letters in length, all caps.

### The Common (*) Environment

The *Common Environment* is a special environment in Clarive that holds Resources and [variables](/concepts/variable)
that are common to every environment or that are not specific to any environment.

For example, the following Resources:

- A GenericServer class Resource may be available to all environments or to only a few. Therefore the common environment
  here means **all**.
- A GitRepository Resource may be assigned to the Common Environment, but actually means **NONE**, since a source code
  repository does not have the concept of environment itself (i.e. you do not create one Git repository for every
environment).

### Legacy: Baseline and bl

Older versions of Clarive had the concept of a *bl*, which translates as *baseline*, although in fact its meaning is
*environment*.

Internally, environment is stored with the name `bl`, and it is thus visible in [YAML](/concepts/yaml) files and other
places.
