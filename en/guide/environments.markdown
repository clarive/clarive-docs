---
title: Environment Modeling
index: 100
---

As part of implementing your complete delivery lifecycle in Clarive, the first step is to define a set of logical
environment definitions that represent the different configuration sets of your physical or virtual infrastructure.

Clarive Environments are a specification of a configuration and its versions with a given state.

- Environments represent the initial starting point of the configuration lifecycle.
- Environments isolate functional work areas. They determine which version of software, services and applications is
  deployed.
- Environments can be configured by project.

Environments can be modeled. Models are a set of configuration variables that can be applied to applications,
microservices, etc. Models are a type of rule that is built by grouping and defining relationships between a given set
of the following:

- Configuration Variables.
- Resources.
- Model Rules.

## Environment Resource

This is the most basic requirement that you need to fulfill at this point. What are your environments? Here are a few
ideas. Note the convention of using all UPPERCASE, short abbreviation environment names. This is recommended because it
improves readability across systems, code and visual components.

- `DEV` - shared development environment, for unit testing individual commits and changesets in a shared space.
- `INT` - continuous (or discrete) integration environment.
- `TEST` - another name for integration test environments.
- `QA` - for testers dealing with functional, system and other environments.
- `UAT` - user acceptance testing environments.
- `TRAIN` - training environment, for training Users with new versions.
- `PRE` - preproduction.
- `PROD` - production.
- `PROD-APAC` - production Asia.
- `PROD-EMEA` - production Europe, Middle-East and Africa.

## Variables

In their most basic structure, Environments are modeled as a set of variables that store the configuration for a given
scope. This scope is normally a Project, which maps an Application.

Variables can hold many data types:

- Text values and textareas.
- Combo and array (list) boxes.
- Passwords (which are automatically encrypted).
- Resources.

Variables are also Resources themselves. This means they maintain relationships in between their values, their scopes,
and the environments to which they have been applied.

## Default Values

For each variable, you set the default value, either for the `Common` environment, or else for individual environments.

To view the default value setting panel, you first need to save the new variable, before reloading the tab.

## Resources

The core of the modeling system is the **Resource**.

Resources hold the set of fields that make up the **Resource**.

Resources can also hold relationships, so that you can define relationships, such as between a Docker container and its
parent Amazon ECS (EC2 Container Service).

## Project (Application) Configuration

Applications can be configured using the Project Resource variable and model field.

For each environment, select one of the environment tabs. Use the `Common` tab for setting global values that are shared
among all environments. For environment-specific variables, set the corresponding variable in the `Variables` field for
each environment.

## Project Environment

A project environment is a Resource that is automatically maintained by the system.

Every time a variable is configured for a project, a relationship is stored between the Project, the Project Environment
and the Environment Resources.

## Defining a Model

The simplest way to describe a model in Clarive is as a group of variables that can be applied to projects so that Users
know what needs to be configured from the outset.

Without models, we would have to basically pick and choose variables from a huge list and then hope we have the correct
ones selected.

Suppose we have to define the model for a Tomcat application:

    host: ${tomcat.hostname}
    port: ${tomcat.port}
    path: ${tomcat.path}
    url: ${tomcat.url}
    home: ${tomcat.home}

This would be a very simple model, but it gives an idea of how things could play out for larger models. We will call
this model "Tomcat Application". In other words, the model defines an application that runs on a Tomcat application
server.

Models are not a mandatory approach to configuring environments, although they are highly recommended.

### Models as Patterns

Normally, organizations will want to create a model or pattern of models for a combination of different technologies
used by its IT. These patterns of models can then be applied to new or existing applications as they are onboarded onto
Clarive.

Here are some examples of models that better represent real-world applications:

- .NET + MSSQL application.
- NodeJS + MongoDB + Docker + ECS containerized microservice.
- Java + Tomcat + Oracle DB.

There are two approaches to defining the model patterns:

- **top-down**: you know how your pattern will look, you declare a set of grouped variables then define the logic
  (rules) that implements it.
- **bottom-up**: you defined loose variables and rules that implement deployment or provision logic. Now you want the
  system to automatically extract it.
