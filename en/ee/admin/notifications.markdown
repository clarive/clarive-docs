---
title: Notifications
index: 4
icon: email
---

The purpose of using Notifications in Clarive is to be able to inform users of events taking place within the tool, be
it the creation of a new Topic, the outcome of a Job or a failed login attempt to the tool. The alert may take one of
two forms:

- Via a message in Clarive, which the user may access in his or her Inbox.
- Via email, enabling the administrator to create his or her own personalized message.

NOTE: To enable e-mail notifications, [email daemon](/ee/admin/daemon) should be active.

Go to Admin - ![](/static/images/icons/email.svg) Notifications to manage Notifications

This shows in the main panel of the Clarive *Notifications* grid and the top bar with the available actions (buttons).

Information is set out as columns, in the following order:

### Events

This is based on the procedure for creating notifications.

In Clarive, notifications are configured by events.

Check the *Event* [...] for further information on the classification of events in Clarive.


### Recipients

Recipients of the notifications. More information below under *Create Notification: Recipients*.

### Scopes

These describe further notification properties. These properties are:

- *Project* - The project defined when creating the notification. This allows you to send notification according to the
  project where the event occurs.
- *Environment* - The environment defined for the notification.
- *Status* - The final status defined for the notification.
- *Step* - The step defined for the notification.
- *Category* - Category topics.
- *Category Status* - Range defined states.

### Action

Action indicates the type of notification: Send or Exclude.

### Active

All notifications may be enabled or disabled.

This column shows the state through a ![](/static/images/icons/start.svg) or ![](/static/images/icons/stop.svg).

All column headers have the same functionality as in the rest of the Clarive panels.

By clicking on the dropdown menu, then *Columns*, we can select the columns to be displayed in the panel.

### ![](/static/images/icons/add.svg) Create

To create a new notification click on the `Create` button.

There are a several options to configure:

- `Event` - The range of events is extensive yet intuitive, because its syntax follows a definite rule: <p style
  = "text-align: center; font-weight: bold"> Example: event.topic.create → event element + action + item </p>

Summarized below:

-*event* - Show the type of notification. In this case are of type **event**.
-*topic* - Indicates the category of the notification.
-*create* - Indicates the action to do.

As a rule, the events are as described below:

*Auth* - Authentication system.

*File* - File.

*Job* - Jobs.

*Post* - Comments.

*Repository* - Events.

*Rule* - Rules.

*Topic* - Topics.

*User* - Comments (creation only).

*Ws* - Web services.

- `Send/Exclude` - Notifications can be set up to be sent or filtered out where appropriate.

The notifications that apply to every event triggered is calculated by an algorithm that first chooses which
notifications apply, then calculates the exclusions to filter out.

- `Template` - HTML templates define the notification interface.

Select the options that start with "generic".

The *generic.html* template is the simplest (a title + body)

- The rest of the templates are created for more concrete elements:
    - *generic_assigned.html* - Specific to `event.topic.modify_field` notification.
    - *generic_post.html* - Notifications about comments.
    - *generic_rule.html* - Notifications about rules.
    - *generic_topic.html* - Notifications about topics.
- `Subject` - You can create a default subject (by leaving *Default* checked) or edit the field. The subject may be:

A simple string.

A dynamic subject, referencing stash variables (for example $ {username}).

- `Recipients` - Using the ![](/static/images/icons/add.svg) Create button select the recipient/s
  notification (may be deleted in this window).
- First combo:
   - *TO*
   - *CC*
   - *BCC*
- Second combo:
  - *Users* - Selects users who receive the notification.
  - *Roles* - Selects the group of users who receive the notification.
  - *Actions* - Selects an action, sends a notification to all users who are assigned projects based on this action.
  - *Fields* - Allows sending of notification to users that are specified in a user combo box fieldlet.
  - *Owner* - Sends a notification to the owner of the topic.
  - *Email* - Sends the notification to the email selected.
* In some cases notifications need additional information about the scope of the event, i.e. the conditions to be met by
  the deployment event.
    - *Job* - Additional field: Project/Environment/Steps. Allows enhancement of notifications system by adding more
      filters to notifications. Steps events have one additional field: 'Step'
    - *Post* - Additional fields: Project/Category/State. This can perform notifications filtering by project, category
      or status.
    - *Topic* - Additional fields: Project/Category/State. This can perform notifications filtering by project, category
      or status.


Each system event has a different scope:

- When left blank on defining the notification, the notification will only be launched if the event also contains the
  empty field.
- When we mark the checkbox *All* to the right of the fields, the condition is met for any value in the event data.


Once all fields are complete, the OK button is selected to create the new notification.

### ![](/static/images/icons/edit.svg) Edit

The notification issue option is activated when you select one from the list (by checking the checkbox to the left of
each row in the *Event* column).

Access the same window with the same fields as the Create menu.

### ![](/static/images/icons/delete.svg) Delete

Erasing notifications.

### ![](/static/images/icons/start.svg) Activate / ![](/static/images/icons/stop.svg) Deactivate

To enable or disable one or more notifications, select the checkbox to the left of each row.

### ![](/static/images/icons/import.svg) Import / ![](/static/images/icons/export.svg) Export

In the tab toolbar, press ![](/static/images/icons/exports.svg).

For **export** just select one or more notifications from the list and click the Export button. The system generates
a [YAML](/concepts/yaml) file with the notification data.

The import option opens a window that allows entry of the exported notification [YAML](/concepts/yaml) and its import.
