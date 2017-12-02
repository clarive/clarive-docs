---
title: Form Rules
icon: rule
index: 1100
---

Form rules is the way to design custom topic category forms in Clarive.

Form work as a visual design tool for forms. With form rules we can define the fields (or __fieldlets__)
that go into a topic category form.

When a form rule runs, the form design is pushed to the stash.
The UI will receive the designed form and translate that into HTML
to be shown to the user.

!!! error "Don't make users wait"
    Do not call complex or slow ops in form rules (like
    an external program/webservice). Users are waiting
    for their topics to be shown and do not expect
    forms to be slow.

### Required Fieldlets

Every form should have at least 2 fields:

- __Title__
- __Status__

The title field holds the topic name and cannot
be removed. The status fieldlet has the current status of
the topic in the workflow.

These 2 fieldlets are automatically included into the
rule after creation.

### Frequently Used Fieldlet Ops

Here's a list of the most useful fieldlets:

#### Description

A long description field that can include `@` user mentions
and `#` references to other topics.

#### Revision Box

Used by changesets to hold repository commits and other change provider
revisions.

#### Topic Selector

For including topics within other topics.

#### User Combo

For adding assignee users, reviewer users and
other assoated user data to the topic.

#### Attach Files

For adding files to the topic.

Please note that every form also automatically
has the following fields:

- The [MID](/concepts/mid), which is the topic ID and cannot be changed by the
  user.
- __Comments__ - not actually a fieldlet. Every topic holds a comment forum
  assoated with it.
