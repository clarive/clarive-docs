---
title: List topics
index: 5000
icon: dashlet-topic-list
---

Lists the selected topics and their status in a ordered list.

There are a list of elements can be configured in the dashlet:

### Height in canvas rows

Defines the height in number of rows given to the dashlet.

The height value will be between 1 and 4 where 4 will occupy 100% of the page.

### Width in canvas columns

Sets the width that the item will occupy in the dashboard.

The maximum allowed value is 12 (100% width).

### Autorefresh

Allows to make the dashlet more dinamic adding an automatic refresh (in minutes).

###  List of fields to view in grid

Allows to select specific fields to view. By default the dashlet will show the followin columns; ID, title, status,
creator and creation date.

This columns can be modify, separating fields (columns) with **;**.

A example to use this field could be:
    `ID_fieldlet`,`column_name`,`type`,`width`;

Where:

- `ID_fieldlet` - Specify the ID_name of the fieldlet.
- `column_name` - Name of the dashlet column.
- `type` - Type of field to show. Can be *text*, *number*, *checkbox* or *Resource*.
- `width` - Set the anchor of the column.

In addition, if we use a **number** type, we can personalize it setting up the number of decimals we want to show, to
make it, just add the number of decimas in parenthesis after type.

#### Types

##### Text

Specify the value is a text.

##### Number

We can use other properties for numbers like `total`. With this property, users can see:

- `sum` - Shows sum of all the values contains in the column.
- `max` - Shows maximum value of all the values contains in the column.
- `min` - Shows minium value of all the values contains in the column.
- `count` - Shows number of rows.
- `currency` - Indicates that we are showing currency, changes the way to show decimals, using US format (. for
  decimals) or standard format (, for decimals). This format is predefined by user preferences.
- `symbol` - Show type of currency;€, $, etc...

Example: `title,Title;created_by, Created By;incoming,My incoming,number(2),,sum,currency,$`

In this example, users can see in the dashlet, a table with the following columns:

            Title  | Created by  | My incoming
            --------------------------------
            Title1 | 2016-02-02  | 23,25 $

##### Checkbox

If we have a checkbox fieldlet in the topic form, we can show an icon instead '1' or '0' to indicate if the checkbox is
marked or not. It's a graphic improvement to show better the status of the fiedlet. To use, just configure a column
like:

Example: `title,Title;created_by, Created By;<check_box_ID>, <Column_name>, checkbox`

##### CI

We can use this type of field if we want to show usernames. By default, Clarive show de ID of the user:

        Title  | Created by  | Owner
        --------------------------------
        Title1 | 2016-02-02  | 1108

. If we want to show the name of the user, just configure the type field to CI:

Example: title,Title;created_by, Created By;owner,Owner, ci

        Title  | Created by  |  Owner
       --------------------------------
        Title1 | 2016-02-02  | admin-1

### Maximum number of topics to list

Set the maximun number of topics to show in the table. By default is set to 100.

If you want to show all topics, just set it to 0.

### Sort by

Set an order by a determinated field (specified by the ID fieldlet).  By default sorts by topic ID.

### Sort order

Indicate ASC or DESC order.

### Show totals row?

Include a last row showing total if we have a number type in the table.

### Select topics in categories

Select one o more categories to show in the grid.

### Select topics in statuses

Select one o more status to configure the table.

### Exclude selected statuses?

Exclude selected classes in the previous combo and show the rest that no selected.

### User assigned to topics

Allow to filter the topics by user assigned or by any user.

### Advanced condition JSON/MongoDB

Allows to use a JSON format o MongoDB query to add a condition.

      {"labels":[],"categories":["*id*"],"statuses":[],"priorities":[],"start":0,"limit":25}

Where *id* is the unique key of the category which can be consulted through the REPL.
