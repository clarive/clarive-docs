---
title: Topic roadmap
index: 5000
icon: dashlet-topic-roadmap
---

Shows a grid with the topic roadmap.

There are a list of elements can be configured in the dashlet:

### Height in canvas rows

Defines the height in number of rows given to the dashlet.

The height value will be between 1 and 4 where 4 will occupy 100% of the page.

### Width in canvas columns

Sets the width that the item will occupy in the dashboard.

The maximum allowed value is 12 (100% width).

### Autorefresh

Allows to make the dashlet more dinamic adding an automatic refresh (in minutes).

###  First weekday

Set the first day of the week to see the roadmap.

### Scale

Set the scale for the roadmap, can be daily, weekly or monthly.

### Environments

Select one o more environments to configure.

### Exclude selected environments?

Show only the environments not selected in the combo above.

### Shift back/foward in days from today to start timeline

Set the days before and after from today.

### Select topics in categories

Select one o more categories to show in the swarm.

### Exclude selected classes?

Show only the clases not selected in the combo above.

### Advanced JSON/MongoDB condition for filter

Allows to use a JSON format o MongoDB query to add a condition.

      {"labels":[],"categories":["*id*"],"statuses":[],"priorities":[],"start":0,"limit":25}

Where *id* is the unique key of the category which can be consulted through the REPL.

### Label mask

Allows to personalize the information will show in the topic mask.

Example: ${category.acronym}#${topic.mid} ${topic.title}
