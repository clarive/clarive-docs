---
title: Roles
index: 5000
icon: role
---

Security within Clarive is handled through a [role system](/concepts/roles).

All access to administrator functions and user functions is defined through roles. Users are thus assigned one or more
roles. That way, the user’s access to Clarive is limited and controlled.

**Example**

An *Administrator* role can be defined and all privileges can be set on administrator functionality within the tool,
such as [Category Administration](/admin/categories), [Notifications Administration](/admin/notifications), [Scheduler
Access](/admin/scheduler), [User Administration](/admin/user), etc. A role *incident manager* can be defined with full
access to the topic category *Incident* but will for instance have no access to topic category *release*, since this
topic category will be managed by the role of *Release manager*.

A user will be assigned one or more roles, and thus inherit the access to the topics he or she can work on.

Role administration can be performed by selecting Admin - ![](/static/images/icons/role.svg) Roles from the menu bar.
This will display all the currently available roles in a list view.

The list view contains the following columns:

- `Role` - The name of the Role.
- `Description` - The description of the role.
- `Mailbox` - The mailbox specific to the role, for [notification](/admin/notifications) purposes.
- `Options` - Summary of all Role actions for this Role.


## Role List Options


## ![](/static/images/icons/add.svg) Create

A new window is opened by clicking on `Create`, in which the following information needs to be provided for
configuration:

- **Role Name** - The name of the Role e.g. *developer*, *release manager*, *change manager*.
- **Description** - A longer description of the Role.
- **Dashboard** - Clarive has several [dashboards](/concepts/dashboards). Dashboards may be associated here with roles,
  such that in [user preferences](/getting-started/prefs) only those dashboards associated with those roles will appear.
The first dashboard to be added will be the default dashboard. Each user may change his or her default dashboard in user
preferences.


### Available Actions

Highlight the user and click `Edit`. All Available Actions attributed to the role are displayed in the left pane.
A Group of actions or a specific action can be added by selecting and dragging the group Action from the left pane to
the right pane.

- `Remove Selection` ![](/static/images/icons/delete-grid-row.svg) - Removes the currently selected Action from
  the Role.
- `Remove All` ![](/static/images/icons/delete-grid-all-rows.svg) - Removes all selections.


## Users that have a Role

Select the *Users* tab to see the users that have the current Role and in which [scope](/concepts/scope) they have the
Role assigned to.

## Scopes where the Role is assigned

This a pivoted version of the User list. Now you see which users have the current Role.

## Actions

Actions are logically grouped. Actions can be added in relation to the following groups:

- `---` - Generic user actions.
    - **User can change his or her password** `action.change_password`. User will be able to change the password from
      the user menu.
    - **Become a different user** `action.surrogate`. User will be able to become any user in the system. Recommended
      only for administrators.
- `admin` - All actions related to the tool administration e.g. topic administration, user administration.
    - **Administer configuration variables** `admin.admin.config_list`. User will be able to set various runtime
      configuration options. Recommended only for administrators.
    - **Administer daemons** `action.admin.daemon`. User will be able to view, edit or admin daemons. See also
      [daemons](/admin/daemon).
    - **Admin events** `action.admin.event`. User will be able to see all the events happening in Clarive.
    - **Admin labels** `action.admin.labels`. User will be able to edit or admin topic labels. See also
      [labels](/admin/labels).
    - **Admin snapshots** `action.admin.snapshots`. User will be able to create, delete or export [snapshots](/admin/snapshot).
    - **Admin notifications** `action.admin.notifications`. User will be able to admin notifications. See also
      [notifications](/admin/notifications).
    - **Admin roles** `action.admin.role`. User will be able to admin user roles.
    - **Root action** `action.admin.root`. User will have the same permissions as system root user. Recommended only for
      administrators. Use this action instead of doing everything under system root user. This will help distinguish
between different administrators.
    - **Admin rules** `action.admin.rules`. User will be able to view and admin rules. It is possible to permit only
      specific rules. See also [rules](/admin/rule-designer).
    - **Admin scheduler** `action.admin.scheduler`. User will be able to admin job scheduling. See also
      [scheduler](/admin/scheduler).
    - **Semaphore Administration** `action.admin.semaphore`. User will be able to view and admin system semaphores.
      Recommended only for administrators.
    - **System messages** `action.admin.sms`. User will be able to send system messages to all users in the system. See
      also [system messages](/admin/system-messages).
    - **Admin topics** `action.admin.topics`. User will be able to admin topic categories. Recommended only for
      administrators. See also [topics](/concepts/topic).
    - **Upgrade features, plugins and modules** `action.admin.upgrade`.  DEPRECATED.
    - **User groups Admin** `action.admin.user_groups`. User will be able to admin user groups. Recommended only for
      administrators.
    - **User Admin** `action.admin.user`. User will be able to admin users.  Recommended only for administrators. See
      also [users](/admin/user).
- `calendar` - All actions related to Job Calendars.
    - **Admin Job Calendar** `action.calendar.admin`. User will be able to admin job calendars. See also
      [calendaring](/admin/calendaring).
    - **Edit Job Calendar** `action.calendar.admin`. User will be able to edit job calendars. See also
      [calendaring](/admin/calendaring).
    - **View Job Calendar** `action.calendar.admin`. User will be able to view calendars. See also
      [calendaring](/admin/calendaring).
- `catalog` - DEPRECATED.
- `ci` - All actions related to configuration items. You can grant permission to manage or view Resources. The action
  Admin Resources also grant permission to view Resources, so it is not neccesary to add both. To specify the Resources,
you have to drag the action. In the new window, select the roles and collections that the user can view/manage. You can
also add negative filters. For example, if the user can see all Resources except the project collection, you can add all
roles and then add a negative filter to that collection.
- `dashboards` - All actions related to Dashboards.
    - **Change dashboards in explorer** `action.dashboards.view`. By default user can see only dashboards that are
      specified in his or her roles. With this action he will be able to see all of them.
- `development` - All actions related to the Development menu on the top bar of the application.
    - **Wipe Cache** `action.development.cache_clear`. User will be able to clear all the application's cached data and
      grid cached data.
      Recommended only for development environments.
    - **ExtJS API References** `action.development.ext_api`. User will be able to see ExtJS documentation.
    - **ExtJS Examples** `action.development.ext_examples`. User will be able to see ExtJS examples.
    - **GUI Designer** `action.development.gui_designer`. DEPRECATED.
    - **JS Reload** `action.development.js_reload`. User will be able to force application to reload all client side
      scripting.
    - **REPL** `action.development.repl`. User will be able to run arbitrary code in application environment.
      Recommended only during development. **DANGEROUS**
    - **Sequences** `action.development.sequences`. User will be able to see database sequences.
- `git` - All actions for accessing the Git Repository.
    - **User can close branches** `action.git.close_branch`. User will be able to omit repository branches from the
      lifecycle panel.
    - **Access git repository for pull/push** `action.git.repository_access`.  User will be able to pull from and push
      to repository.
    - **Access git repository pull** `action.git.repository_read`. User will be able to pull from a repository.
    - **Can update system tags in repositories** `action.git.update_tags`. User will be able to move the system tags
      (environments) in repositories.
- `help` - Actions related to the Help menu.
    - **View server info in About window** `action.help.server_info`. User will be able to see more detailed information
      in About window.
- `home` - Actions associated with the tool such as allowing access to the Lifecycle panel or the main menu.
    - **User can generate docs from topics and views** `action.home.generate_docs`. DEPRECATED.
    - **User can access the menu** `action.home.show_menu`. User will be able to see the main menu.
    - **User can access the repositories in a project** `action.home.view_project_repos`. User will be able to see the
      repositories assigned to the project in the lifecycle panel.
    - **User can access the releases view** `action.home.view_releases`. User will be able to see the Releases tab in
      lifecycle panel.
    - **User can access the workspace view** `action.home.view_workspace`.  DEPRECATED.
- `job` - All actions related to jobs e.g. creating new jobs, restart jobs. See also [job](/concepts/job).
    - **Can access the advanced menu in job detailed log** `action.job.advanced_menu`. User will be able to access
      internal job stash. Recommended only for administrators.
    - **Approve/Reject any Job** `action.job.approve_all`. User will be able to approve or reject jobs. See also
      [monitoring](/admin/monitoring).
    - **Cancel Jobs** `action.job.cancel`. User will be able to cancel jobs. It is possible to assign it only to
      specific environment.
    - **Change default pipeline in job new window** `action.job.chain_change`.  User will be able to change the pipeline
      during new job creation. Recommended only for administrators.
    - **Change job status on Post step** `action.job.change_step_status`. User will be able to change the job status. It
      is possible to assign it only to a specific environment.
    - **Create new jobs** `action.job.create`. User will be able to create new jobs. This involves any kind of
      deployments and promotions.
    - **Delete job** `action.job.delete`. User will be able to delete a job. It is not recommended that jobs be deleted.
      It is possible to assign it only to a specific environment.
    - **Force Rollback** `action.job.force_rollback`. User will be able to rollback job even if the rollback is not
      needed. It is possible to assign it only to specific environment.
    - **Create jobs outside of available time slots** `action.job.no_cal`. User will be able to create jobs outside
      available [Calendar Slots](/admin/calendaring).
    - **Restart Jobs** `action.job.restart`. User will be able to restart jobs.  It is possible to assign it only to
      a specific environment.
    - **Resume Jobs** `action.job.resume`. User will be able to resume jobs. For example from PAUSE state. It is
      possible to assign it only to specific environments.
    - **Run Jobs In-Proc, within the Web Server** `action.job.run_in_proc`. User will be able to run the jobs within the
      web server process. No need for the dispatcher to be running. Recommended only during development.
    - **View job monitor** `action.job.view_monitor`. User will be able to see the Job Monitor.
    - **View All Jobs** `action.job.viewall`. User will be able to see jobs in the Job Monitor. It is possible to assign
      it only to specific environment.
- `labels` - Action allowing to attach/remove labels.
    - **Attach labels to a topic** `action.labels.attach_labels`. User will be able to attach labels to the topics.
    - **Remove labels to a topic** `action.labels.remove_labels`. User will be able to remove labels from the topics.
- `projects` - Action allowing to access the Project Lifecycle.
    - **User can access the project lifecycle** `action.project.see_lc`. User will be able to see the project lifecycle
      in lifecycle panel.
- `reports` - Actions allowing to view dynamics fields and reports.
    - **View dynamic fields** `action.reports.dynamics`. User will be able to see dynamic report fields.
    - **View Reports** `action.reports.view`. User will be able to see Reports panel in lifecycle panel.
- `search` - Actions allowing to search for Jobs, Resources and topics.
    - **Search CIs** `action.search.ci`. User will be able to search through Resources.
    - **Search jobs** `action.search.job`. User will be able to search through jobs.
    - **Search topics** `action.search.topic`. User will be able to search through topics.
- `topics` - Allows the user to view topics, delete topics, create a topic, add comments to the topics, etc. Once the
  action is drawn, you can filter so the user can only apply that action for given categories.
    - **View Topic Activity** `action.topics.activity`. User will be able to see the topic activity. This includes all
      the changes to the topics data during its lifetime.
    - **Post/View Topics Comments** `action.topics.comments`. User will be able to see comments and add comments.
    - **Create Topic** `action.topics.create`. User will be able to create a topic of all categories or a specific
      category.
    - **Delete Topic** `action.topics.delete`. User will be able to delete a topic of all categories or a specific
      category.
    - **Edit Topic** `action.topics.edit`. User will be able to edit a topic of all categories or a specific category.
    - **View Topic jobs** `action.topics.jobs`. User will be able to see all the jobs that involved this topic.
    - **Change topics status logically (no deployment)** `action.topics.logical_change_status`. User will be able to
      change the topic status without starting a job if this is required by the topic workflow.
    - **View Topic** `action.topics.view`. User will be able to see a topic of all categories or a specific category.
    - **View related graph in topics** `action.topics.view_graph`. User will be able to see topic relationship graphs.
- `topicfields` - Allows configuration of the actions to see and/or edit the fields of the topics. It is possible to
  configure each field depending on the category and the status of the topic.  Simply add the category, status and the
field so the user can interact with it. It is also possible to perform negative filters, for example, provide a user
permission to view all fields of a category minus the *Estimate* field. To do this, assigned permissions to see all the
fields in that category and add a negative filter to the *Estimate* field.

### ![](/static/images/icons/edit.svg) Edit

Allows editing the selected Role. Once changes have been made, select the *Accept*. To discard any changes, select the
*Close* button instead.

### ![](/static/images/icons/copy.svg) Duplicate

Allows duplication of the selected Role. A new Role is created with the same values as the original Role. Its initial
name will be the name of the original Role concatenated with a number.


### ![](/static/images/icons/delete.svg) Delete

The selected Role will be deleted. The system will provide a confirmation message before actually deleting the Role. If
users exist with that Role, the Role will be removed from the user.

Also, list search is available to look for Roles by Role or description.
