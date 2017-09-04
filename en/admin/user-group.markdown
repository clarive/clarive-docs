---
title: User Group
index: 5000
icon: users
---

User groups allow administrators to manage the roles assigned more easily. As soon as a user belongs to at least one
group, its security definition will be managed from thegroup. Changing the group roles will change the users assigned to the group.

If a user belong to more than one group, the user security will be the result of merging the security of all groups the
user belongs to.

The list view contains the following columns:

- `Name` - Full name of the user group.
- `Users`- List of group members.

### ![](/static/images/icons/add.svg) Creating a User Group

- `Group` - Name of the Group.
- `Users` - List of users that belong to the group.

You must save the entered data before assigning Roles and Projects.

Under these fields, the Roles defined in the database are displayed on the left, and the available
[scopes](/concepts/scope) this user might be assigned a role for are displayed on the right.

**IMPORTANT NOTE**: Assigning Roles is only available to saved groups.  So save first before adding roles to a group.

To add a Role or multiple roles for a user, mark the checkbox(es) next to the role in the left panel, in the right pane
select either ALL projects, or one or multiple Clarive projects by marking the checkbox next to all or next to one or
more Clarive scopes.  Click on the bottom left button to add the project related roles for that group.

In the bottom window the roles assigned to that group for the scopes selected.

To Unassign roles/projects from a group, there are several options.

A few examples:

- To unassign the Role *Developer* for all Clarive Projects from the group, mark the row and click on ![](/static/images/icons/delete-grid-row.svg)
- To unassign the Role *Developer* from the Clarive Project *ClientApp* from the group, mark the checkbox next to
  *Developer* in the left pane, mark the checkbox next to *ClientApp* in the right pane and click on  ![](/static/images/icons/key-delete.svg)
- To unassign all Roles for the Clarive Project *ClientApp* from  a group, mark the checkbox next to *ClientApp* in the
  right pane, click on ![](/static/images/icons/key-delete.svg)
- To unassign all Roles from a group, click on ![](/static/images/icons/delete-grid-all-rows.svg)

### ![](/static/images/icons/edit.svg) Editing a Group

Allows the Administrator to modify existing data for the selected group.


### ![](/static/images/icons/delete.svg) Deleting a Group

The selected group will be deleted. The system will provide a confirmation message before deleting the group.

### ![](/static/images/icons/copy.svg) Duplicating a Group

Allows duplication of the selected group. A new Group is created with the same values as the original.
