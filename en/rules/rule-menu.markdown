---
title: Rule Menu
index: 4000
icon: rule
---

The way to access rule stuff is through Admin menu. Selecting **Admin - ![](/static/images/icons/rule.svg) Rule
designer** a new tab appears with three different areas. From left to right:

### Rules grid area

Area with two columns and an action tab:

- **Rule** - Rule id, rule name and rule type.
- **Time** - Last modification time.

### Actions

Actions defined are:

- ![](/static/images/icons/add.svg) **Create** - Use to start a configure a new rule.
- ![](/static/images/icons/edit.svg) **Edit** - Edit selected rule.
- ![](/static/images/icons/delete.svg) **Delete** - Delete selected rule.
- ![](/static/images/icons/catalog-folder.svg) **Tree view** - Organise the rules based on the type.
- ![](/static/images/icons/restart-new.svg) **Activate** - Activate selected rule.
- ![](/static/images/icons/exports.svg) **Tools** - ![](/static/images/icons/import.svg) Import or
  ![](/static/images/icons/export.svg) Export the rule to other Clarive system in [YAML](/concepts/yaml) format.

### Rule tree

Area where selected rule is displayed as a tree, it has an **action tab with some operations**, they are:

- ![](/static/images/icons/refresh.svg) **Refresh** - To refresh the rule
- ![](/static/images/icons/save.svg) **Save** - To save rule.
- ![](/static/images/icons/ok.svg) **Check** - To check rule (see [Quality Analysis](/concepts/rule-quality-analysis)).
- ![](/static/images/icons/edit.svg) **DSL** - Raises up a new window with DSL code from the rule selected. This code
  can be executed. This functionality will be described in the [rule palette](/rules/rule-palette) page.
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

### Rule Debug Panel

Debug panel ![](/static/images/icons/debug-view.svg) is shown when there are any issues found with the rule. There it is
possible to see the operation that caused the problem and a short description.

### Palette

Contains all operations (ops) that can be used for rule composition.

It has an action tab with two action:

![](/static/images/icons/search-small.svg) **Search** - To find a rule with a mask as input.

![](/static/images/icons/refresh.svg) **Refresh** - To refresh the palette

If the parameter *show_in_palette* is set to one in the JS config file, the operation defined will be available in the
palette.
