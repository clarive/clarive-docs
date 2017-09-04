---
title: Users
index: 5000
icon: user
---

Clarive Users are stored directly in the Clarive Database. Even if external authentication is used, Users must be
created in the Clarive Database in order for login to work.

User administration can be performed by selecting Admin - ![](/static/images/icons/user.svg) Users from the menu bar.
This will display all the currently available Users in a list view.

The list view contains the following columns:

- `Avatar` - The User's avatar.
- `User` - User ID of the user, used for logging into the system.
- `Name` - Full name of the user.
- `Alias` - Alias for the User ID.
- `Language` - The selected User language.
- `Modified on` - Date of the last modification made to the user.
- `Email` - Email address of the User.
- `Phone` - Phone number of the User.
- `Type` - Indicates the type of account the user has.

### ![](/static/images/icons/add.svg) Creating a User

- `User` - The User ID the User will use to log into Clarive Software.
- `Account type` - Sets the type of account. There are two types:
   - Regular - For all Users, who can use Clarive with all their functionalities.
   - System - Users that cannot log in or surrogate but can be used in Rules. These Users are not counted for the User
     limit per license.
- `Password` - The password the User will use in combination with the User ID to log into Clarive.
- `Confirm Password` - The password the User will use in combination with the User ID to log into Clarive.
- `Alias` - An Alias for a User.
- `Name` - Full name of the User.
- `Phone` - Phone number of the User.
- `Email` - Email address of the User.

You must save the entered data before assigning Roles and Projects.


Under these fields, the Roles defined in the Database are displayed on the left, and the available
[Scopes](/concepts/scope) this User might get a Role for are displayed on the right.

**IMPORTANT NOTE**: Assigning Roles is only available to saved Users.  Be sure to save first before adding Roles to
a User.

**IMPORTANT NOTE 2**: If a User belongs to any group, its security cannot be managed individually and it will be the net
result of merging the security of all the groups it belongs to.

To add a Role or multiple Roles for a User, highlight the User and click Edit, then mark the checkbox(es) corresponding
to the Role in the left pane (Available Roles), and in the right pane (Available Projects) select either *All*, or one
or multiple Projects by marking the checkbox next to one or more Clarive Scopes.

Click on the bottom left button *Assign roles/projects* to add the Project-related Roles for that User.

In the bottom window the Roles assigned to that user for the Scopes selected are shown.

To Unassign Roles/Projects from a User, there are several options.

A few examples:

- To unassign the Role *Developer* for all Clarive Projects from the User, mark the row and click on
  ![](/static/images/icons/delete-grid-row.svg)
- To unassign the Role *Developer* from the Clarive Project *ClientApp*  from  the user, mark the checkbox next to
  *Developer* in the left pane, mark the checkbox next to *ClientApp* in the right pane and click on
![](/static/images/icons/key-delete.svg)
- To unassign all Roles for the Clarive Project *ClientApp* from  a User, mark the checkbox next to *ClientApp* in the
  right pane, click on ![](/static/images/icons/key-delete.svg)
- To unassign all Roles from a User, click on ![](/static/images/icons/delete-grid-all-rows.svg)


Once you have roles assigned to a user, you can use this configuration to create a new **user group**.  Click on
![](/static/images/icons/copy.svg "Copy roles to new group") ``Copy roles to new group`` button right under
**Roles/Projects** window.  This function is useful if you need to assign the same roles to another user.

### ![](/static/images/icons/edit.svg) Editing a User

Enables the Administrator to modify existing data for the selected User.

### ![](/static/images/icons/suspend-user.svg) Suspending an User

The selected User will be suspended/unsuspended. The system will provide a confirmation message. A suspended users, can not do anything in Clarive until
they are unsuspended again.
For deleting an user completely, this must be done from user resource grid.

### ![](/static/images/icons/copy.svg) Duplicating a User

This allows duplication of the selected User. A new User is created with the same values as the original.

### ![](/static/images/icons/prefs.svg) User Preferences

The administrator can change User Preferences, such as language or avatar by selecting a User and clicking on the
Preferences button.

### ![](/static/images/icons/surrogate.svg) Surrogate

The administrator can take the User profile

### ![](/static/images/icons/envelope.svg) Inbox

Allows access to the User mailbox.

### ![Licensing](/static/images/icons/about.svg) Licensing

Clarive is generally licensed on a named User basis, except for ELA (Enterprise Level Agreements) licenses.

Creating new Users will usually consume one of such licenses, except in the case the User is **inactive**.

Check your license file for details on your User limits.

### ![](/static/images/icons/suspend-user.svg) Hide Suspended Users

Clicking this button, you can show only users that are not suspended.
