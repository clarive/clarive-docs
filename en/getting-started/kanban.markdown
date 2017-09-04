---
title: Topic Kanban Board
index: 5000
icon: board
---

Clarive has a Kanban board generator utility that is available from two places:

- The Topic grid
- From within a Topic that holds other Topics.

The Kanban board can be opened by clicking on the following icon: ![](/static/images/icons/board.svg)

### How does it work?

Clarive Kanban boards are always initialized either from within a list of Topics (from the grid) or from the Topics
contained within a Topic.

From that list, the Kanban will show as tables all from and to Statuses available as immediate Topic Transitions
(transitions that can be performed for the Topics shown). Likewise, the Environments corresponding to those Statuses are
displayed directly below them.

It will hide Statuses that the User cannot transition to or from, or that are not available as a Transition.

To change the [Status](/concepts/status) of a Topic, just drag and drop the Topic to another Status, except for
promotable Environments (see below). When an element being dragged may be dropped, this is shown by a box with broken
lines as the element passes over the column belonging to the status concerned. When a Topic is dropped into another
Status column, that becomes the new Status of the Topic.

## Toolbar

**Selection mode**

This may be done in two ways; either by searching via the search field, where listed topics matching the entered pattern
will be highlighted in yellow, or else by clicking on activate manual selection, where we will click on the topics we
wish to select.

Once selected, we will be able to perform different actions on them:

- Delete selected topics.
- Delete unselected topics.
- Select all.
- Unselect all.

**Add topics**

This allows us to add topics of any category to the Kanban board.

**Columns**

This allows us to customize the Kanban display, with the option of showing/hiding statuses, showing only topics,
environments statuses, etc.

**Views**

This allows us to display different viewing modes for that Kanban.

- FootPrint: Displays topic history with status changes and the time it has been in topic in each state. This time can
appears in three different colors, green, yellow or red. These colors are always the same, however they appear when the
topic are too much time in the same state. To configure when to show a topic in yellow or red, it is necessary to access
the [Categories administration](/admin/categories) and configure the SLA tab.

**Save**

This allows us to save the Kanban with our customizations. We can save this, either creating a new Kanban, or
overwriting the current one.

**Maximize/Minimize**

This allows to maximize/minimize the Kanban to fit the screen in order to optimize display.

**Reset configuration**

This allows to return to the initial display before applying any changes.

**Fullscreen**

This allows us to view the Kanban in fullscreen.

**Close Kanban**

This allows us to close Kanban.

### Promote / Demote to Environments

Topics that are associated with environments have the environment name(s) at the top.

If a Topic gets dragged into a promotable Environment, a new job window will pop up.  Schedule the Job accordingly. When
the Job runs, the pipeline will take care of deploying the changeset contents and promoting the Topics into (or demoting
them out of) the destination Environment and corresponding Status.  once successfully completed, the topic will appear
under the new status.

### Promote / Demote to Environments

Topics that are associated with environments have the environment name(s) at the top.

If a Topic gets dragged into a promotable Environment, a new job window will pop up.  Schedule the Job accordingly. When
the Job runs, the pipeline will take care of deploying the changeset contents and promoting the Topics into (or demoting
them out of) the destination Environment and corresponding Status.  once successfully completed, the topic will appear
under the new status.

### Customizing the Kanban Board

Kanban boards can be customized by adding or removing status columns.

These customizations can be saved by clicking the `Save Layout` button, which is only available for Kanban boards
generated within Topics. Topic grid boards do not have this option.
