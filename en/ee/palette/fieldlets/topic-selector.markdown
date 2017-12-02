---
title: Topic selector
index: 5000
icon: fieldlet-system-list-topics
---

Allows to add topics to the form.

Also allows to create topics clicking on ![](/static/images/icons/add.svg) Create button.

There are a list of elements can be configured in the fieldlet:

### Section to view

Indicates where the fieldlet will be in the Summary view of the Topic.

- **Header** - Shows the fiedlet in the middle of the page.
- **More info** - Shows the fiedlet in a new tab 'More info' in the bottom of the page.
- **Details** - Shows the fiedlet in the right part of the page.

### Row width

Allows to personalize the anchor of the fieldlet in **Edit topic**.

The maximum allowed value is 12 (100% width of the tab).

### Row height

Allows to personalize the height of the fieldlet in **Edit topic**.

The maximum allowed value is 12.

### Hidden from view mode

Indicates if the field will be hidden from the view mode.

### Hidden from edit mode

Indicates if the field will be hidden from the edit mode.

### Mandatory field

Check if you want the field as mandatory.

### Type

Allow to set the type of the field.

- **Single** - Allows to select one choice of the options available.
- **Multiple** - The user can select multiples choices.
- **Grid** - The added topics are shown in a table.

### Display field

Set the field to show.

By default is Title the value to show in the combo.

### Advanced filter JSON

Allows to use a JSON format to add a condition.

For example, to show only a category user can use the filter:

    {"labels":[],"categories":["*id*"],"statuses":[],"priorities":[],"start":0,"limit":25}

Where *id* is the unique key of the category which can be consulted through the REPL.

It is also possible to apply date intervals to limit results. To use this, is necessary to make use of the commands *lt*
and *gt* own by MongoDB.

    {"ts": {"$gt":"2016-03-22","$lt":"2016-04-08" } }

### List of columns to show in grid

Select the columns to show in the grid.

Default columns displayed are the topic name (shows the category and ID) and title of the topic. To define a column, put
id of the field we want to show, title of the column and type of the fields. All this options have to be separated by
comma and diferent columns with semicolon. If we want a field which is a date we can especify the type as datetime if we
want date and time, or just date if we only want the date.

*Only works if Grid is set in the type of field.*

### Page size

Defines the number of elements will appear.

*Only works if Grid is set in the type of field.*

### Parent field

Select the parent field of the topics.

### Filter field

Specify a condition to the selector. This is a combo with every fieldlets that are in the form.

### Filter data

Specify a condition to the data.

This field is required if previous field is not empty.

### Filter type

Specify the logic of the filter.

By default, filter type is OR.

For more information, there is a how-to called [Filters in fieldlets](/ee/how-to/filter-fieldlet).

### Grid Page Size

Defines number of topics to show in one page of the table.

### Table format

Allows to configure when show the table controls in View mode.

- **Always**
- **Only if paging**
- **Never**

### Sort By

Set the topic property to order the table in view mode (title, created_on, modify_by, etc.)

By default it sort by topic MID.

### Sort Order

Set to sort ASC or DESC.

### Custom Columns

Allows to add personalize columns in the fieldlet when type is Grid.

- **Id Column** - The Id of the column. This field is mandatory and can not be changed.
- **Display Column** - The name of the column. If is not defined, the column will be called with the id.
- **Column Type** - Can be text or a variable. This field is mandatory and can not be changed.
- **Variable** - This field is mandatory if column type is variable. You can select a variable of type combo or array.
  Edit the value of a cell clicking two times on it.
