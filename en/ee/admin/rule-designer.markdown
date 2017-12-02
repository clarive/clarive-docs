---
title: Rule Designer
icon: rule
index: 120
---

The Clarive *Rule Designer* is the interface for designing, prototyping,
writing and testing Clarive rules.

This document describes how to use the rule designer interface.
For specific details on how to implement specific rules, head
over to the (creating rules)[/rules/creating-rules] document.

The Rule Designer is divided into 3 specific area:

- __Rule explorer__ - navigate through available rules in the system
- __Rule editor__ - edit a rule content
- __Rule palette__ - list available _ops_ for dragging and dropping

## Rule Explorer

The rule explorer shows the list of rules available in the
system. The rule explorer has 2 modes: list and tree.
The mode can be changed with the list/tree button
in the button panel.

Every rule has a `name` and an `id`.
Also the modified time and the last modifier username
is shown in the list.

### Actions

Actions defined are:

- ![](/static/images/icons/add.svg) **Create** - Use to start a configure a new rule.
- ![](/static/images/icons/edit.svg) **Edit** - Edit selected rule.
- ![](/static/images/icons/delete.svg) **Delete** - Delete selected rule.
- ![](/static/images/icons/catalog-folder.svg) **Tree view** - Organise the rules based on the type.
- ![](/static/images/icons/restart-new.svg) **Activate** - Activate selected rule.
- ![](/static/images/icons/exports.svg) **Tools** - ![](/static/images/icons/import.svg) Import or
  ![](/static/images/icons/export.svg) Export the rule to other Clarive system in [YAML](/concepts/yaml) format.

## Palette

The palette contains all available ops in the system.

!!! note "What are ops anyway?"
   Clarive __ops__ (from operations) are the elements that give a rule its
   functionality. They have been called tasks or actions, but we think ops,
   with just 3 letters, is a better, if not geeky, name for such tiny bit of
   functionality.

Depending on what plugins and features are installed,
there may be more or less ops available to the user.

It has an action tab with two action:

![](/static/images/icons/search-small.svg) **Search** - To find a rule with a mask as input.

![](/static/images/icons/refresh.svg) **Refresh** - To refresh the palette

If the parameter *show_in_palette* is set to one in the JS config file, the operation defined will be available in the
palette.

#### Palette Ops

It is divided in seven types of tasks:

1. **Statements** -Provide control flow rule, they are IFs and Fors, and ad- hoc tasks.
2. **Services** - Operating in the pass,  they can be:
   - *Job Services* - Tasks associated to a job.
   - *Generic Services* - General type.
3. **Workflow** - All services related to workflow rules.
4. **Blueprint** - All variables created as a [Resource](/concepts/variable) that user can use in Blueprint rules.
5. **Rules** - Allow including rules within other rules, these rules to be include have to be of independent type.
6. **Dashlets** - Use to build [dashboards](/concepts/dashboards).
7. **Fieldlets** - Fieldlets that shape the form.

## Rule Editor

The rule editor (central) panel is where the rule logic
can be created and modified.

It's also the drag-and-drop destination for palette ops.
Drag and drop ops from the palette into the rule editor to get
started.

### Rule Tree Area

Area where selected rule is displayed as a tree, it has an **action tab with some operations**, they are:

- ![](/static/images/icons/refresh.svg) **Refresh** - To refresh the rule
- ![](/static/images/icons/save.svg) **Save** - To save rule.
- ![](/static/images/icons/ok.svg) **Check** - To check rule (see [Quality Analysis](/concepts/rule-quality-analysis)).
- ![](/static/images/icons/edit.svg) **DSL** - Raises up a new window with DSL code from the rule selected. This code
  can be executed. This functionality will be described in the [rule palette](/ee/rules/rule-palette) page.
- ![](/static/images/icons/wrench.svg) **Tools** - Some additional options:
   - **Regular expression** - Allow to search a regular expression.
   - **Ignore case** - Activate/Desactivate case sentitive to search text.
   - **Blame by time** - Mark the changes in the elements by a specific period of time.
   - **Variables** - Show rule [variables (Resources)](/concepts/variable).
- ![](/static/images/icons/expandall.svg) **Expand all** : Expands every single rule in any job step.
- ![](/static/images/icons/collapseall.svg) **Collapse all** - Collapse every rule and step, just viewing start point.
- ![](/static/images/icons/slot.svg) **Version** - Expands all history versions from the rule selected. The output shows
  date, time and user who saved the rule. It is possible here to add tags to one or more previous versions of the rule
by right-clicking on each selected version, selecting `Add tag`, and entering a name in the *Tag* field. This makes it
possible to revert back to an earlier version in the event of an error occurring when [deploying
Topics](/getting-started/deploy-topics) using the latest version.
- ![](/static/images/icons/logo-html.svg) **HTML** - Displays in another navigator tab, op properties values and
  configuration from every op included in the selected rule.
- ![](/static/images/icons/workflow.svg) **Flowchart** - Displays tree of the rule

### Rule Runner

The rule runner is a debug panel ![](/static/images/icons/debug-view.svg) shown
when there are any issues found with the rule. It's possible to see the operation
that caused the problem and a short description.

### Creating a Rule

When creating a rule, the rule creation wizard opens.
The user has to decide first which type of rule to create,
type a name and configure the rule.

There are many types of rules that can be created using the Rule Designer.
These are the available rule types in Clarive:

- [Independent](/ee/rules/independent)
- [Webservice](/ee/rules/webservice)
- [Event](/ee/rules/event)
- [Pipeline](/ee/rules/pipeline)
- [Form](/ee/rules/form)
- [Workflow](/ee/rules/workflow)
- [Dashboard](/ee/rules/dashboard)
- [Report](/ee/rules/report)
- [Blueprint](/ee/rules/blueprint)

Read more about the different rule types in the [creating rules](/ee/rules/creating-rules)
documentation.

The rule creation options can be changed later if needed with the
`Edit` button.
