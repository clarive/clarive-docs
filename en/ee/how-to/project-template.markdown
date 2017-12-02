---
title: Create a Project Template
index: 5000
icon: ci-project-template
---

Every Project can have a set of [Variables](/concepts/variable) with values set specifically for that Project, and
indeed for every [Environment](/concepts/environment), each of which can hold values, such as strings, numbers, lists,
hashes (dictionaries) and Resources (e.g. Natures and Blueprints).

Setting them can be a time-consuming process, and it is often the case that different Environments have the same ones,
albeit with different values. Project configuration can be streamlined by grouping Project Variables in a *Project
Template*, in which the one to which they are available is also set. Those from a Project Template are referenced in
Projects in a similar way to when referencing said Variables directly.

## Creating a Project Template

Select ![](/static/images/icons/ci-project-template.svg) ProjectTemplate in the menu bar Resources/All. Then select the
![](/static/images/icons/add.svg) Create button.

Enter a name into the `Name` combo, then select from the `Variables` combo the ones previously defined that you would
like to include in the Project Template. These will appear in the order in which they were selected (and in the format
in which they were created, such as value, textarea, combo etc.) below the `Copy Vars To...` combo. If a different
Environment is selected from `Copy Vars To...` the current one will change to the one to which the variables are to be
copied.

Click `Save` before changing Environment in the respective combo. On switching from one to another, the Variables
created for the previous one will no longer be listed below the `Copy Vars To...` combo. Repeat the above steps for as
many Environments as you need to select Variables for.

### Copy Variables

Should you need the same (or a similar) set of Variables for more than one Environment, it may be easier to copy these
between them, once you have your set in a given Environment.

In order to do this, select the target Environment from the `Copy Vars To...` combo. Note that the Variables will
contain the same values as in the one in which they were created. These can be changed here. In the case of combo-type
ones, you may select one of the other options available in the previous Environment.

Any that are not needed may be deleted from the set.

Click `Save`.
