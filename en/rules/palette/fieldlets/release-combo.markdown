---
title: Release combo
index: 5000
icon: fieldlet-system-release
---

Allows to introduce a combo box with the releases availables in the form.

There are a list of elements can be configured in the fieldlet:

### Section to view

Indicates where the fieldlet will be in the Summary view of the Topic.

- **Header** - Shows the fiedlet in the middle of the page.
- **Body** - Shows the fiedlet in the top right of the page.
- **More info** - Shows the fiedlet in a new tab 'More info' in the bottom of the page.

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

### Select topics in categories

Select one o more categories of type Release to show.

### Select topics in statuses

Select one o more status to configure the table.

### Exclude the statuses selected

Exclude the statuses selected and shows the remainder are **not** selected.

### Type

Allow to set the type of the field.

- **Single** - Allows to select one choice of the options available.
- **Multiple** - The user can select multiples choices.
- **Grid** - The added topics are shown in a table.

### Display field

Set the field to show.

### Advanced filter JSON

Allows to use a JSON format to add a condition.

For example, to show only a category user can use the filter:

    {"labels":[],"categories":["*id*"],"statuses":[],"priorities":[],"start":0,"limit":25}

Where *id* is the unique key of the category which can be consulted through the REPL.

It is also possible to apply date intervals to limit results. To use this, is necessary to make use of the commands *lt*
and *gt* own by MongoDB.

        {"ts": {"$gt":"2016-03-22","$lt":"2016-04-08" } }

### Release field

It establishes dependence between this Release topics type and dependent topics.

It is through this field which should be completed by the ID field in the form of the dependent topics.

### Filter field

Specify a condition to the release combo.

This is a combo with every fieldlets that are in the form.

This field is required if next field is not empty.

### Filter data

Specify a condition to the data.

This field is required if previous field is not empty.

### Filter type

Specify the logic of the filter.

By default, filter type is OR.

For more information, there is a how-to called [Filters in fieldlets](/how-to/filter-fieldlet).
