---
title: Calendar
index: 5000
icon: dashlet-topic-calendar
---

Shows the calendar in the dashboard.

There are a list of elements can be configured in the dashlet:

### Height in canvas rows

Defines the height in number of rows given to the dashlet.

The height value will be between 1 and 4 where 4 will occupy 100% of the page.

### Width in canvas columns

Sets the width that the item will occupy in the dashboard.

The maximum allowed value is 12 (100% width).

### Autorefresh

Allows to make the dashlet more dinamic adding an automatic refresh (in minutes).

### Calendar query

Indicate what activity or issue will show in the calendar. The options are:

- **Topic Activity** - Allows to view topic ativity of selected topics from creation to modification.
- **Open topics** - Shows open topics from creation to final statuses.
- **Calendar planner** *(eg: Milestones or Environment planner)* - Show schedulers with job slots o specific milestones.
- **Own fields** - Personalize the fields to show, for example, if user want to see only a specific range of dates. Need
  to specify two fields:
  - *Initial date*.
  - *Final date*

### Default View

Establish the default view of the calendar:

- **Month** - Shows a month view by default.
- **Basic week** - Show the complete week (from Sunday to Monday)
- **Schedule week** - Show the week divided by hours.
- **Basic day** - Only shows the present day.
- **Schedule day** - Shows the present day divided by hours.s

### First weekday

Select the first day of the week to see the calendar.

### Select topics in categories

The option gives to user the chance to select the topics that will appear in the calendar view

### Exclude selected categories?

Show only the categories **not** selected in the combo above.

### Show jobs?

If the user has permissions it shows the jobs scheduled in the calendar.

### Advanced JSON/MongoDB condition for filter

Allows to use a JSON format o MongoDB query to add a condition.

      {"labels":[],"categories":["*id*"],"statuses":[],"priorities":[],"start":0,"limit":25}

Where *id* is the unique key of the category which can be consulted through the REPL.

### Label mask

Allows to personalize the information will show in the topic mask.

Example:

      ${category.acronym}#${topic.mid} ${topic.title}
