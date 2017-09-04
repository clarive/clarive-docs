---
title: Topic
index: 5000
icon: topic
---

The *Topic* is Clarive's central delivery lifecycle entity.

Clarive is not just about the technical components put in releases.  Organizations that use Clarive manage logical
"documents" called *Topics* that handle the different aspects of their delivery process. This may include different
types of releases, sprints, etc.  These documents have [workflows](/concepts/workflow) which can represent many
different **logical** states and changes are attached to these Topics. They also have fields, with role-based security
and actions.

A *Topic category* is an organization-defined form instance that has an associated workflow. Think of it as a template.

A *Topic* is an instance of the Topic category, that has an assigned [MID](/concepts/mid).

### Topic Category

Every Topic category in Clarive can have any number of fields, a workflow with statuses and transition
[Rules](/concepts/rule) or constraints, as well as [Dashboards](/concepts/dashboards) for context filtered insight and
reporting.

A Topic category typically has the following properties:

-  A set of [statuses](/concepts/status).
-  A [workflow](/concepts/workflow).
-  A form [Rule](/concepts/rule), with its defined fieldlets.
-  Field-level security
-  Transition-level security: which user/roles can transition a [Topic](/concepts/topic) from one status to the next.
-  A color, for visual representation of the category.
-  An acronym, to easily represent the Topic category name.
-  A discussion.

Some Topic categories may be:

-  Release
-  Changeset
-  Issue
-  Bug or Defect
-  Test Case
-  Estimation
-  Request
-  Sprint
-  User Story
-  Product Backlog

Changesets, and any other Topics, can be grouped into releases. Having Topics grouped in releases is the key to
fully-fledged orchestration of the delivery lifecycle.

### Why Topics?

We believe that every installation must have full control over how their process is defined. Therefore having standard,
out-of-the-box entities in a delivery lifecycle tool actually interferes with the ground-up thinking that is needed to
have the most adapted process.

Topics are great for both brownfield and greenfield implementations, as they can ajust and adapt to existing processes,
but also help define new, unconstrained processes that can best represent the organization's needs.
