---
title: Topics burndown NG
index: 5000
icon: dashlet-topic-ng
---

Show a trending line with the real topics and the predicition.

There are a list of elements can be configured in the dashlet:

### Height in canvas rows

Defines the height in number of rows given to the dashlet.

The height value will be between 1 and 4 where 4 will occupy 100% of the page.

### Width in canvas columns

Sets the width that the item will occupy in the dashboard.

The maximum allowed value is 12 (100% width).

### Autorefresh

Allows to make the dashlet more dinamic adding an automatic refresh (in minutes).

### Chart will be shown as

It shows the different types of graphics that can be used:

- Area
- Area step
- Lineal
- Bar
- Scatter

### Topic date field

Set the date range based on topic field. Fill the field with the fieldlet ID.

### Scale

Can be set to hours, days, months or years.

#### Date selection method

Pick the dates selection to show in the X-Axis. Can be:

- By duration - Select the range and the offset to show dates.
- By period - Choose the first date and the last day you want to appear in the X-Axis.
- By topic filter - Choose the fieldlet id to select the desired dates.

### Select topics in categories

Select one o more categories to show in the grid.

### Close statuses

Select one o more status to configure the table.

### Custom JSON query

Allows to use a JSON query to add a complex condition.

      {"labels":[],"categories":["*id*"],"statuses":[],"priorities":[],"start":0,"limit":25}

Where *id* is the unique key of the category which can be consulted through the REPL.

## Options as a fieldlet

Clarive allow the user to add this dashlet inside a topic as a tab.

The behaviour is the sames as a dashlet.

Only two options are different:

- Width - Set, in %, the width of the dashlet.
- Height - Set in px, the height of the dashlet.
