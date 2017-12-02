---
title: Statuses and Transitions
index: 5000
icon: state
---

A *Status* is a [Resource](/concepts/resource) that represents the state of an issue at a particular point in a specific
[workflow](/concepts/workflow). An issue can be in only one Status at a given point in time.

When defining a Status, you can optionally specify properties. Read more about them in the [status
administration](/ee/admin/status) page.

### Transitions

A *Transition* is a link between two Statuses that enables an issue to move from one Status to another. In order for an
issue to move between two Statuses, a Transition must exist.

A Transition is a one-way link, therefore if an issue needs to move back and forth between two Statuses, two Transitions
need to be created. The available workflow Transitions for an issue are listed on the View issue screen.

### Status Types

There are five Status types:

- **New** - Indicates that a [Topic](/concepts/topic) has just been created and has not been picked up by the team.
- **Cancelled** - Indicates an aborted status.
- **Closed** - Indicates that the Status is probably the last one in the flow.  By setting a Status to Closed, we are
  preventing the Topics in this state from being shown in most views, such as Topic lists / grids and Kanbans.
- **Deployable** - Means that, as part of a Transition into this Status (promote), Changeset Topics need to be deployed
  to one of the associated [Environments](/concepts/environment). As part of the Transition out (demote), Changeset
topics need to be backed-out from the environment.
- **Generic** -s Any other Statuses fall into this category.

### Promote

*Promote* Transitions in Clarive are meant to represent Transitions to Deployable states.

### Demote

Demote Transitions, on the other hand, generate backout Transitions, with a [Rollback](/concepts/rollback)
[Job](/concepts/job).

### Changing a Topic's Status

Click `Change Status` to open a dropdown menu containing all the Lifecycle Statuses available to the current Topic.
These are listed in a logical order of progession through the Topic Lifecycle. After changing the Topic's Status, close
and re-enter the Topic in order to view the new Status in any of the Lifecycle modes.
