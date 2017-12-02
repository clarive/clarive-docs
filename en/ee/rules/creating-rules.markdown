---
title: Creating Rules
icon: rule
index: 130
---

The first step in creating a rule is selecting the rule type.

- [Event](/ee/rules/event)
- [Pipeline](/ee/rules/pipeline)
- [Independent](/ee/rules/independent)
- [Webservice](/ee/rules/webservice)
- [Form](/ee/rules/form)
- [Workflow](/ee/rules/workflow)
- [Dashboard](/ee/rules/dashboard)
- [Report](/ee/rules/report)
- [Blueprint](/ee/rules/blueprint)

Each rule type serves a distinct purpose and can accept or not certain types of
ops from the palette.

But in general we can divide rule types in 2 distinct groups: return rules
and action rules.

### Action Rules

Action rules are meant to run code the interact with the external
world, implying what is called _side effects_, like copying files, calling
webservices.

But by definition, the variables in their stash values are primarily ignored,
with some known exceptions such as Webservice rules.

These are:

- Independent rules called from other execution rule types or used in a
  scheduler.

- Event rules, triggered with events, are used for event control and event-related
  tasks.

- Pipeline rules hold the tasks that run in deployment jobs.

- Webservice rules, invoked from an URL into the system.

### Return Rules

These rules have as purpose configuration return data into the stash. This data
is then used to compose views in the product, such as forms, dashboards,
reports or control workflow behavior.

- Form rules return form metadata in the stash.

- Workflow rules return workflow structure and decisions.

- Dashboard rules return stash data with a list of dashlets, their
  configuration and position in the dashboard.

- Reports return metadata and data to be loaded into a data table in the UI.

- Blueprints are a set of variables that compose a template definition for
  configuring environments.

- Independent rules may fall into this category also, as they could hold reusable
  rule ops, say a set of form fields.

### Compilation mode

This field controls how your rule is going to
be compiled into the system.

- __None__ the rule will be compiled on-demand.
This has a (usually small) performance penalty but allows for quicker
system start.

- __Precompile__ precompiled rules are compiled when the system starts.
For example, when the Dispatcher or Web Server starts. It has a startup
penalty and can **slow job execution start**. On the other hand,
Do not use this option when developing a rule, creating frequent versions
of it.

### Getting Started

For starting with rules, we recommend creating a simple __Independent Rule__.
Try dragging and dropping ops into the rule. Then hit the `Run` button to
open the Run panel.

Steps:

1. Create an independent rule and give it a name, ie `Foo`

2. Drag and drop the `LOG` operation from the palette

3. Double click on the dropped log operation to open the
`Configuration` panel. Optionally, right-click on the
`LOG` op to get the op context menu and select the
`Configuration` option.

4. Put `Hello world` into the `Text` field and Save (Ctrl/Cmd-S)
to close the window.

5. Select the `Run` button on the button bar. This will open the
runner console underneath your rule. Hit the `Run` button again
for it to compile and run your rule.

Voilà! You have just created and run your first rule.
