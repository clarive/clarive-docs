---
title: Categories
index: 5000
icon: topic
---

Category management is located within the Administration options - ![](/static/images/icons/topic.svg) Categories.

### General interface

The list view contains the following columns:

- `Checkbox column` - The checkbox needs to be selected for the editing buttons to become activated. Note that multiple
  selections can be made, but that certain buttons are only available.
- `Category` - The name and the color of the Category as it will be shown in the topics.
- `ID` - The master ID (mid) of the Category within Clarive.
- `Acronym` - The short notation used when creating instances of this Category class. Can be configured inside Category options.
- `Description` - Short description of this Category class.
- `Type` - Type of Category.
    * *Normal* - this is a normal discussion topic that is used to collaborate in the Lean Application Delivery process.
  Examples are Requirement, Change Request, Test  Scenario, etc.
    * *Changeset* - A changeset Topic is used to track changes to assets that are part of the application delivery process.
    * *Release* - This is a Topic that is used to releasing/deploying to certain environments.to tie/assign (code) changes
  to. The following actions buttons are available above the list of Topics:

### ![Create Category](/static/images/icons/add.svg) Create

Create a new Category.

Clicking on `Create` opens a new window with all the options to create a custom category.

- `Category` - Textfield. Name of the new Category.
- `Acronym` - Textfield. Indicates the moniker of the new Category.
- `Description` - Textarea. Short description to explain the definition and purpose of the topic.
- `Type` - The type of Category in a DevOps Context. This can be either Normal, Changeset or Release (see also above).
- `Pick a Color` - Select the color to be used for this Topic. Colors support better visibility.
- `Default Grid` - This option allow to use report as a customized grid in order to view the data of the topic.
- `Form`  - is the [form](/rules/rule-concepts) that is assigned to the topic.
- `Dashboard` - This option allow to put a Dashboard in topic view.
- `Provider` - Specifies the provider of the Topic. This can be either internally created or any of the available
  integrations, such as for example Bugzilla/Basecamp/Trac/Redmine/BMC Remedy/Jira/HP PPM/Clarity.
- `Options` - Currently only one option is available: make the topic read only.  This is used only for integrations to
  avoid overwrite of information.
- `Status Grid` - Select the different statuses this topic can have.  The grid shows the available statuses (as defined
  under configuration items-ci-status) and their description. Select statuses by making the corresponding checkboxes.
  Maintaining a Status is explained in a separate chapter “Maintaining Statuses”

### ![Delete Category](/static/images/icons/delete.svg) Delete

All the Categoryes that have their checkbox selected will be deleted.

The system will provide a confirmation message before actually deleting the Categoryes.

The Category can not be deleted as long as there are instances for that topic in the database.  The instances should be
inspected first and deleted before the Category can be deleted, assuring database integrity.

###![Edit Category](/static/images/icons/edit.svg) Edit

Allows editing the selected Category. Note that this button is only available when a single Category has been selected.
Once changes have been made, select the “Accept”.  To avoid any changes, select the “Close” button instead.

###  ![Duplicate Category](/static/images/icons/copy.svg) Duplicate

Allows duplication of the selected Category class. Note that this button is only available when a single Category has
been selected. A new Category is created with the same values as the original class. Its initial name will be the name
of the original Category with a number. After duplicating a Category it is **advisable** to edit and change the name,
description and other elements that can cause confusion between the original and the duplicate category.

### ![Import_export](/static/images/icons/exports.svg) Import/Export

The system allows you to import and export the selected Categories in case you want to copy existing categories from one
system to another.

Clicking on ![Export](/static/images/icons/export.svg) Export, a new window will open with the [YAML](/concepts/yaml)
code of the selected categories.

Clicking on ![Import](/static/images/icons/import.svg) Export, a new window will open where you paste the generated code
during export.

Once clicked on `Import` you can see the progress and status of the import at the bottom of the window.

### Edit the Workflow of the selected Category

Allows editing of the workflow restrictions of the selected Category.  Note that this button is only available when
a single Category has been selected.

Workflow restrictions are tight to a specific role defined within Clarive.

The workflow editor window will show all available roles in the top left window.  To create the possible transitions per
role, you first select the role(s) that can make the status transition, then you select the status from where the
transition starts (the dropdown “Status from”), then in the listbox under the status from, you can select all the status
that are allowed for the selected roles.  Once ready you hit ![](/static/images/icons/down.svg) to add the selected
transitions to the list shown in the bottom part of the window.

In case you want to remove certain transitions,you can select for which roles, which transitions need to be removed
(same way as for adding as described above), but you then hit ![Remove](/static/images/icons/clear-all.svg) to remove
the transitions from the list.
