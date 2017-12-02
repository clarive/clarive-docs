---
title: Topic charts
index: 5000
icon: dashlet-topic-chart
---

Shows a pie with the status of the topics.

There are a list of elements can be configured in the dashlet:

### Height in canvas rows

Defines the height in number of rows given to the dashlet.

The height value will be between 1 and 4 where 4 will occupy 100% of the page.

### Width in canvas columns

Sets the width that the item will occupy in the dashboard.

The maximum allowed value is 12 (100% width).

### Autorefresh

Allows to make the dashlet more dinamic adding an automatic refresh (in minutes).

### Select or type the grouping field

Select the fiedlets to group the topics.

### Chart will be shown as...

Can show a different views of the chart

- Pie
- Donut
- Bar

### Grouper number field

We can group topics by their numeric fiedlet.

### Minium % to group series in Others group

Set the lower value to group topics in 'Other' group. Decimals can be used.

### Type of number

Set the type of number defined in the Grouper number field option.

### Currency symbol to be shown

User can add a symbol at the end of the number like $ or €.

### Agregate grouper field by

Allow show operations like average or total.

### Max characters in legend

Allow to set number of max characters to show in legend.

### Order by legend

Sort by legend

### Select topics in categories

Select one o more categories to show in the swarm.

### Select topics in statuses

Select one o more status to configure the table.

### Advanced JSON/MongoDB condition for filter

Allows to use a JSON format o MongoDB query to add a condition.

      {"labels":[],"categories":["*id*"],"statuses":[],"priorities":[],"start":0,"limit":25}

Where *id* is the unique key of the category which can be consulted through the REPL.

### Depth

Select the depth range (1-5) in search of topics. This field is used only in the dashboards inside of topics.
