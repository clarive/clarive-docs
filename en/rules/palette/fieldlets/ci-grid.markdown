---
title: CI Grid
index: 5000
icon: fieldlet-ci-grid
---

Allows to introduce a Resources grid in the form.

There are a list of elements can be configured in the fieldlet:

### Section to view

Indicates where the fieldlet will be in the Summary view of the Topic.

- **Header** - Shows the fiedlet in the middle of the page.
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

### Type

The type of the field is **Grid** by default. It means that the added topics are shown in a table.

### Display field

Set the field to show.

By default, title of the Resources is shown.

### Advanced filter JSON

Selectable fields to filter can be found through the REPL. In this case the command would be: `CI-> project-> find_one
();`

It is also possible to apply date intervals to limit results. To use this, is necessary to make use of the commands *lt*
and *gt* own by MongoDB.

        {"ts": {"$gt":"2016-03-22","$lt":"2016-04-08" } }

### Selection method

You specify the values that appear in the form. Two types to choose from:

- **Role selection** - Select the role to be displayed on the form, regardless of class. For example, if we choose
  Agent, in the form we will see all Agents, *ftp_agent*, *clax_agent*, etc...
- **Class selection** - We can specify class of the Resource.

### Default value

To show a default value in the box.

### Filter field

Specify a condition to the CI grid.

This is a combo with every fieldlets that are in the form.

This field is required if next field is not empty.

### Filter data

Specify a condition to the data.

This field is required if previous field is not empty.

### Filter type

Specify the logic of the filter.

By default, filter type is OR.

For more information, there is a how-to called [Filters in fieldlets](/how-to/filter-fieldlet).

### Description

Selection of type of description to show in the list.

- **Name** - Show the name.
- **Environment** - Show the Environment separated by commas.
- **Class** - Show the type object.
- **Moniker** - Show the moniker specified in the Resource configuration.


### Height

Set the height of the grid in Edit topic mode.
