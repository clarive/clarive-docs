---
title: Workflow
index: 5000
icon: workflow
---

A Clarive workflow is the set of [statuses](/concepts/status) and transitions that a [Topic](/concepts/topic) goes
through during its lifecycle.

There are two types of workflows:

- Topic-based, which are for simple workflows
- Rule-based, for complex or reusable workflows

### Topic Workflows

These are simple workflows that apply to a given [Topic category](/ee/admin/categories).

### Rule Workflows

Typically, most topic categories will do fine with just a simple, topic workflow.

Rule workflows should be used instead for complex decision transitions:

- Project specific flows
- Field-dependend transitions, ie. if "urgency" fieldlet value is "urgent" then skip "promote to QA"
- External dependent workflow decisions, like calling an external webservice to determine where or how to promote the
  topic.
- Field content checks conditional, such as checking that a given field has been filled-out before allowing promotion to
  happen.

### Reusability

Also, rule workflows are useful as **reusable workflows**. One workflow rule may be reused in many different topic
categories.
