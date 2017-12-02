---
title: Topics timeline
index: 5000
icon: dashlet-topic-dateline
---

Shows a timeline with the number of topics.

There are a list of elements can be configured in the dashlet:

### Height in canvas rows

Defines the height in number of rows given to the dashlet.

The height value will be between 1 and 4 where 4 will occupy 100% of the page.

### Width in canvas columns

Sets the width that the item will occupy in the dashboard.

The maximum allowed value is 12 (100% width).

### Autorefresh

Allows to make the dashlet more dinamic adding an automatic refresh (in minutes).

### Select topics in categories

Select one o more categories to show in the chart.

### Select topics in statuses

Select one o more status to configure the table.

### Exclude selected statuses?

Show only the statuses not selected in the combo above.

### Shift in days from today to start/end timeline

Set number of days from/to today to start/end timeline.

### Advanced JSON/MongoDB condition for filter

Allows to use a JSON format o MongoDB query to add a condition.

      {"labels":[],"categories":["*id*"],"statuses":[],"priorities":[],"start":0,"limit":25}

Where *id* is the unique key of the category which can be consulted through the REPL.

### Date field in topics to use as X axis

Select the date field to use in X axis the graphic timeline.

### Chart will be shown as...

Indicate what type of chart will be shown.

- Area
- Area step
- Line
- Bar
- Scatter

### Data grouped by

Select the criteria for grouping data.
