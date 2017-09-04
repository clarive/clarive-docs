---
title: CI Graph
index: 5000
icon: dashlet-ci-graph
---

Shows a CI Graph in the dashboard.

There are a list of elements can be configured in the dashlet:

### Height in canvas rows

Defines the height in number of rows given to the dashlet.

The height value will be between 1 and 4 where 4 will occupy 100% of the page.

### Width in canvas columns

Sets the width that the item will occupy in the dashboard.

The maximum allowed value is 12 (100% width).

### Autorefresh

Allows to make the dashlet more dinamic adding an automatic refresh (in minutes).

### Graph type

Indicate what type of graph can be used. The options are:

- Space tree
- Radial Graph
- D3 Force-Directed graph

### CI as Graph Starting Point

Select one o more Resources as a start point.

### Override CI with current context

Allows to override Resource view by a current topic or project or see Resource always.

### Show Toolbar?

Allows to display in the dashboard the dashlet toolbar where you can set parameters such as the chart type, add an
additional filter or print the chart.

### Incluir clases

Shows the selected classes in the CI Graph.

### Exclude selected classes?

Exclude selected classes in the previous point and show the rest that **no** selected.

### Advance condition JSON/MongoDB

Allows to use a JSON format o MongoDB query to add a condition.

      {"labels":[],"categories":["*id*"],"statuses":[],"priorities":[],"start":0,"limit":25}

Where *id* is the unique key of the category which can be consulted through the REPL.
