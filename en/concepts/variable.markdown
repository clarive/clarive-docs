---
title: Variable
index: 5000
icon: ci-variable
---

A *variable* in Clarive is a globally defined [Resource](/concepts/resource) belonging to the class variable.

Each variable can hold values, like strings, numbers, lists, hashes (dictionaries) and Resources.

Variables can be referenced in [Rules](/concepts/rule) using the notation `${variable-name}`.

When a rule runs, its [stash](/concepts/stash) is loaded with global variable default values. Then, as the rule
advances, either variable values change or new variables are introduced to the stash.

## Mandatory variables

Every variable can be set to mandatory. This affects the project variables (see [Project](/concepts/project) for more
info).

## Blueprint Variables

Blueprint Variables contain other Variables configured within a Blueprint Rule. In order to make this set accessible
outside the Blueprint (e.g. to [Project Templates](/ee/how-to/project-template)), we first need to create a new Variable,
and set its `Type` to 'CI', and its `CI Role` and `CI Class` to 'Nature' in the respective combos. We must then create
a Nature as a container for the selected Blueprint.

## Copy variables

When copying variables between environments (see [Project](/concepts/project) for more info) if this flag is set the
value of the variable is also copied.

## Project Variables

Every [Project](/concepts/project) can have a set of variables with values set specifically for that Project. Moreover,
for every [Environment](/concepts/environment), different values can be set.

Variables may be configured in an [Project Template](/ee/how-to/project-template) according to the Environment(s) in which
they are available or are assigned a given value.
