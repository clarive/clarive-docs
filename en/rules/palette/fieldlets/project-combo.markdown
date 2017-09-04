---
title: Project combo
index: 5000
icon: fieldlet-system-projects
---

Allows to introduce a combo box with the projects in the form.

There are a list of elements can be configured in the fieldlet:

### Section to view

Indicates where the fieldlet will be in the Summary view of the Topic.

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

### Advanced filter JSON

Allows to use a JSON format to add a condition.

        {"labels":[],"categories":["*id*"],"statuses":[],"priorities":[],"start":0,"limit":25}

Where *id* is the unique key of the category which can be consulted through the REPL.

It is also possible to apply date intervals to limit results. To use this, is necessary to make use of the commands *lt*
and *gt* own by MongoDB.

        {"ts": {"$gt":"2016-03-22","$lt":"2016-04-08" } }

### CI Class

Specify the class of Resource to be shown.
Tipically the Resource Class to use in this fieldlet is *project*.

### Default value

To show a default project in the box.

### Roles

Selection of roles to show in the grid.

### Description

Selection of type of description to show in the list.

- **Name** - Show only the name.
- **Environment** - Show the name and the environments separated by commas.
- **Class** - Show the name and the type object.
- **Moniker** - Show the name and the moniker specified in the Resource configuration.
