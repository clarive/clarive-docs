---
title: Resource Grids
index: 5000
icon: class
---

[Resources](/concepts/resource) are a fundamental aspect of configuration in Clarive, and they can be managed in Grids,
which consist of lists of a given type of item that the User can view.

Grids can be accessed by selecting the `All` menu option in the Resources menu, followed by the item type. As well as
being directly selectable in the menu, specific item types are also grouped under more generic menu nodes e.g.
Environment is listed both individually and under `Internal`.

Other examples of Resources include servers, User IDs, agents, middleware (such as JBoss or Apache), cloud instances,
mainframe nodes etc.

### Sorting

By default a Grid sorts by earliest to most recent Timestamp.

To change the sort direction, click on the title of the desired column.

### Searching

Resource Grids can be also filtered by using the Clarive [Search Syntax](/getting-started/search-syntax).

#### Create

Resources can be created directly in the relevant Grid by clicking the `Create` button on the Action bar. This opens
a creation-mode tab containing further viewing, editing and deletion options for that individual item.

#### Edit

Changes can made by clicking on the listed item in the Grid, which opens it in an edit-mode tab, which contains similar
options to creation mode.

#### Delete

The `Delete` button allows deletion of the selected item(s).

#### Export

Clarive allows the User to export the Grid as YAML, JSON, HTML or CSV, using the `Export` button on the Action bar.

#### Import

Similarly, the User may import the respective Grid as YAML or CSV, using the `Import` button on the Action bar.

#### Class Services

The `Class Services` button opens a drop-down menu from which a custom service may be selected for running simultaneous
instances of the same type.

An example of this could be a window containing a series of functions such as buttons for running the service, tabs,
output panes etc., depending on the type of items concerned.

#### Show Graph

The `Show Graph` button opens a tab for displaying the item in a variety of [graph](/concepts/ci-graph) formats in
relation to others, such as Project, User etc.
