---
title: Topic Grid
index: 5000
icon: topic
---

The Topic Grid is the list of Topics that the User can see.  Its concept is based on an email inbox.

The Topic Grid can be viewed within Clarive in three initial modes:

- **All Topics** - Opened by selecting the `All` menu option in the Topic menu.
- **By Category** - Opened by selecting a category under the Topic menu.
- **By Status** - Opened by selecting a status under the Topic menu.
- **By Project** - Opened by clicking on the Project name under `Projects` ![](/static/images/icons/project.svg) in the left pane.

### Sorting

By default the Topic Grid sorts by most recently modification date.

To change the sort direction, click on the Title of the desired column. Each click will reverse the sort direction
(ascending/descending).

#### Create Like

When you select one topic in the grid and then click the button Create Like, a new topic will appear filled with the
data of the previous one, but it needs to be saved to create it.

### Searching

The Topic Grid can be also filtered by using the Clarive [Search Syntax](/getting-started/search-syntax).

### Filtering

To filter which Topics are shown, use the right-side selector pane.

#### Filter types

Each filter has three states:

- **Checked** - Show Topics with this status.
- **Crossed** - Hide Topics with this status.
- **Unselected** - Hide Topics with this status (if there is another Status checked) or show Topics with this Status (if
  there is no other Status checked).

Therefore, if no Status is checked or crossed, then all Statuses are shown.

The user will be able to combine the filters as he wants, being these the options that will be found:

##### Filters

Filter the list according to:

- Modified today: Shows only the topics that have been modified during the last 24 hours.
- Created today: Shows only the topics that have been created during the last 24 hours.
- Assigned to me: Displays the topics where the "assigned" field (a [user combo
  fieldlet](/ee/palette/fieldlets/user-combo)) is filled with the name of the user of the active session.
- Unread: Shows the topics that the user with the active session has not read.
- Created by me: Shows only the topics that have been created by the user.

##### Add date

Allows you to add a range of dates to perform the search, these dates can be opened leaving one of the two fields blank.
In addition, a combo is shown to filter the date depending on when the topic was created (*"Show me the topics created
between one date and another"*) or when they have been modified (*"Show me the modified topics between one date and
another"*).

##### Add user

Allows filtering by the user or users who have created or modified the topics (*Show me the topics that have been
created by User1 and User2*).

##### Categories

Filter by the Category the user wants to see. If none is selected, it displays all available Categories.

##### Statues

Filter the grid of topics by statuses, adding as many as the user wishes. Clarive by default displays an 'Open' status
which encompasses all [Initial, Generic and Deployable type statuses](/ee/admin/status).

##### Projects

Filter the list of topics according to the projects to which the topic belongs. Allows you to add as many filters as the
user wants.

##### Labels

Displays only the topics with the labels selected in the filter. From this grid you can assign available labels to
topics dragging the label from the filter to the topic.

##### Parent

Allows the user to add one or more topics, Clarive will return the parent topics of the filtered topics. (*Show me the
topics to which topic #1108 belongs.*)

#### Reset Grid columns

Restore Topic Grid columns showing default columns and hiding those added by the user, using the `Reset Grid Columns`
button on the Action bar.

#### Export

Clarive allows the User to export the Topic Grid as HTML, CSV or YAML, using the `Export` button on the Action bar.

#### Open Kanban

Clicking on the `Open Kanban` button on the Action bar shows the Topics Grid in [Kanban view](/getting-started/kanban)

#### Collapsed Rows

Clicking on the `Collapse Rows` button on the Action bar allows viewing of more Topics per page, albeit with less
information.
