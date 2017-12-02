---
title: Workflow Rules
icon: rule
index: 1110
---

Workflow rules define the behavior of how topics change states.
When creating a topic category, admins can select to use
either a static workflow or a worflow rule (available as a drop
down in the [Categories](/ee/admin/categories) administration panel).

Workflow rules are composed with topic status decisions
that can use control ops (`IF`s, `FOR`s, ...) and
stash variables.

!!! info "When to use Workflow rules"
    Workflow rules should be used for implementing complex status change workflows
    that __depend on topic data__, such as the `project` it belongs to.
    If your workflow is dead simple, just use the simple workflow designer
    available in the [Categories](/ee/admin/categories) panel.

### Recommendations

We recommend using as many `Workflow` palette as possible and
use as little `CONTROL` operations as possible. Keep the workflow
simple and neat so that it can be understood by users.

The reason for this is that the user sometimes will click on
the topic workflow diagram button to understand your workflow.
The graphical representation of a Workflow rule is an exact
match of each op in your rule.

- Give meaningful names to your ops

- Don't use the almighty `Change Topic Status If Matches` op, because it
can potentially hide away the workflow in one big black box. If you
use it, put a long op name that describes what it does.
