---
title: Custom Form Fields
index: 2200
---

Rulebooks can be used to add custom fields to topic forms.
Every time a topic is opened, the form renderer engine
first checks for the existence of form field rules and executes
them.

!!! note
    This only works for topics that have its project field assigned.
    Otherwise, the custom field system would not know which rulebook
    to apply from many different projects.

    If you need a custom field to be applied globally, the project
    to which your rulebook belongs must be a global project.

## Form field rules

Form field rules are made of a sequence of ops, just like any
other rule in Clarive. But instead of executing commands or
sending files remotely, _form field rules output field definitions
called __fieldlets__._

There are special form field events that we can create rules for.

The following list of events may be different, depending on the
profile(s) installed in Clarive SE. In Clarive EE the set of
customizable form events may be completely different since new events
can be defined at the administrators discretion.

Event                          | Description
-------------------------------|----------------------------------------------------------
any_form                       | adds a field to all forms
form_feature                   | adds a field to feature form types
form_bugfix                    | adds a field to bugfix forms
form_sprint                    | adds a field to sprint forms
form_release                   | adds a field to release forms
form_epic                      | adds a field to sprint forms
form_hotfix                    | adds a field to hotfix forms
form_story                     | adds a field to story forms
form_task                      | adds a field to task forms
form_task_template             | adds a field to task template
[custom_category]\_form        | adds a field to custom category forms (Clarive EE only)

For example, to add different fields to the bugfix topic form, use the
following rulebook structure:

```yaml
name: my custom fields

bugfix_form:
   - field_text:
        label: "Estimated duration"
        id: estimated_duration

sprint_form:
   - field_text:
        label: "Estimated duration"
        id: estimated_duration
```

For conciseness, you can group field definitions with the `def` op.

```yaml
name: grouped custom fields

def:
   time_management:
       - field_text:
             label: "Estimated duration"
             id: estimated_duration
       - field_date:
             label: "Estimated end-date"
             id: enddate

bufix_form:
    - time_management:

sprint_form:
    - time_management:
```

You can even parametrize the fields with variables to make
it more adaptable.

```yaml
name: grouped custom fields

def:
   time_management (show_date):
       - field_text:
             label: "Estimated duration"
             id: estimated_duration
       - if: {{ show_date }}
         then:
           - field_date:
                 label: "Estimated end-date"
                 id: enddate

bufix_form:
    - time_management:
          show_date: false

sprint_form:
    - time_management:
          show_date: true
```

## Available Fieldlets

- __field_text__ - simple text field

- __field_date__ - simple date field

- __field_time__ - simple time field

- __field_textarea__ - a multiline text field

- __field_richtext__ - rich HTML-based text editor

- __field_combo__ - a drop-down combo box with a static list of options

- __field_pills__ - selectable visual options

- __field_grid__ - a multi-column table

- __field_upload__ - an attachment field

## Getting the form context

In every form event rule, the following variables are available.
These variables are useful in making the fields conditional to things
like security or topic situation.

Variable            | Description
--------------------|-------------------------------------------------------
username            | id of the user opening the topic
category            | name of the topic category
topic_mid           | mid of the topic (not available if it's a new topic)

```yaml
any_form:
    - if: "{{ ctx.status('name') == 'In Progress' }}"
      then:
         - field_text:
              label: Assigned Tester
              id: tester
```

## Common Arguments

Every `field_*` type op has a set of common arguments that can be
used to configure the form field.

Argument            | Required? | Type        | Default
--------------------|-----------|-------------|-----------------------
`id`                | required  | string      | -
`label`             | required  | string      | -
`colspan`           | optional  | num (1-12)  | 12 (max width)
`rowspan`           | optional  | num ( >2 )  | (according to field)
`default`           | optional  | any         | -
`required`          | optional  | bool        | false
`edit`              | optional  | bool        | true
`view`              | optional  | bool        | true
`active`            | optional  | bool        | true
`readonly`          | optional  | bool        | false

#### label (required)

Label is the text that show up next to the field.

#### id (required)

When the topic data is stored in the database, it's stored
with a field id.

Field ids are important as you may want to use them later
in other event or pipeline rules to extract configuration
data from them.

Field ids have to be __all lowercase, start with alpha characters (from a to z)
and be followed by any character from alphanumeric characters and underscore__.

Example ids:

- `my_field` (ok)

- `_my_field` (not ok)

- `2017field` (not ok)

- `someField` (not ok)

!!! tip
    Prefix all your fields with a recognizable identifier
    so that you can easily remember them while keeping the database organized.
    Also, use snake notation (underscore separators) for more clarity.

    For instance, if your fields were related to work estimates they could
    be prefixed with the string `estimate_`, such as `estimate_date`,
    `estimate_description` etc.

#### colspan

Number of columns that the field will occupy in the edit mode, a number from 1 to 12.

#### rowspan

Number of rows that the field will occupy in the edit mode, minimum is 2.

The form grid layout manager will try to accomodate the fieldlet
within the grid, which also takes into consideration the rows of other
fields visible.

#### default

Default value for the field.

#### required

If a field is required (set to `true` or to `1`, the topic can only be saved if
the field has data.

#### edit

Boolean that determines if the field can be seen in the topic editor panel.

Set `edit` to false if the field should not be visible in the editor panel.
Default is true.

#### view

Boolean that determines if the field can be seen in the view panel of the topic
(main panel). Default is true.

#### readonly

Boolean that determines if the field can be __modified__ in the edit mode.
Default is false, meaning a field can always be modified.

## Field ops

#### field_text

This field will create a simple, one line text field.

```yaml
any_form:
    - field_text:
        id: next_version
        label: Next Version String
```

#### field_textarea

A text field that is multi-line. The text has no formatting.
For a formatted text field, use the `field_richtext` op instead.

Use the `rowspan` parameter to configure the field height.

```yaml
any_form:
    - field_textarea:
          id: test_description
          label: Test Case Description
          rowspan: 8
```

#### field_richtext

This opens a rich HTML-based text editor, which supports text and paragraph
formatting, visual queues, such as lists and image pasting.

```yaml
any_form:
    - field_richtext:
          id: test_description
          label: Test Case Description
          rowspan: 8
```
#### field_date

A date field which opens a calendar.

```yaml
any_form:
    - field_date:
          id: target_date
          label: Target Date
```

#### field_time

A time field.

```yaml
any_form:
    - field_time:
          id: target_date
          label: Select Delivery Time
```

#### field_pills

Pills are option buttons that are highlighted in color and
shown as badges.

Pills are great for short selection lists (from 2 to 4) that are also very easy
to see and click. Each option should have at least the parameter `name:` and
optionally `color:`.

```yaml
any_form:
    - field_pills:
          id: issue_type
          label: Issue Type
          options:
           - name: High
             color: e0a0a0
           - name: Low
             color: a0a0e0
```

#### field_grid

Grids are a multi-column table that holds sub-fields.  You can define from one
to many columns, but try to limit columns to 4 or 5 max, otherwise it may not
fit into users screen properly and may become difficult to read.

```yaml
any_form:
    - field_grid:
         label: Testing Issues Detected
         id: testing_issues
         columns:
             - name: "By Whom"
               type: users
             - name: "Which Project"
               type: projects
             - name: Verified?
               type: checkbox
               default: true
               width: 20
             - name: Verified?
               type: checkbox
             - name: "Problem Type"
               type: combo
               default: "Translations"
               options:
                   - Code
                   - Documentation
                   - Translations
```

Each column accepts these common parameters:

Parameter      | Description                                         | Default
---------------|-----------------------------------------------------|---------------------------------------
`id`           | The column id used to store into the db             | If no id set, name is converted to id
`name`         | The column header text                              | (required)
`type`         | Type of field for the column (list of types below)  | textfield
`width`        | The column width in pixels                          | 100
`default`      | The default value for the field                     | (none)
`sortable`     | If the column is sortable or not                    | true
`readonly`     | If the column is readonly                           | false

This is the set of column types to pick from:

Column Type    | Description                                        | Additional Options
---------------|----------------------------------------------------|---------------------------------------
`textfield`    | single line text                                   | none
`textarea`     | multi line text                                    | none
`checkbox`     | A simple checkbox                                  | none
`combo`        | A simple checkbox                                  | `options: [ 'column1', 'column2' ]`
`date`         | A date picker                                      | none
`projects`     | Drop-down list of all projects in the system       | none
`users`        | Drop-down list of all users in the system          | none
`environments` | Drop-down list of all environments in the system   | none

To set a default value to a column field, just add `default:` to the list of options.

```yaml

    # ...

    - field_grid:
         label: Testing Issues Detected
         id: testing_issues
         columns:
             - name: "Issue Type"
               type: combo
               default: "External"
               options:
                  - "Internal"
                  - "Documentation"
                  - "External"
```

#### field_combo

This is a drop-down combo with a fixed set of values passed as an array in the
parameter `options`.

To set a default value, use the name of the option.

```yaml
any_form:
    - field_combo:
        label: Select Speed
        default: Faster
        options:
            - Faster
            - Slower
```

#### field_upload

This field enables users to upload one or more files.
Files uploaded are attached to the topic and are stored in
the database.

```yaml
any_form:
    - field_upload:
        label: Upload Evidence Files
        id: evidence_files
```

## Additional Form Ops

There are also a few additional form ops
that allow your rulebook to control existing fields, like
removing predefined fields from view or make them readonly.

#### remove_fields

The `remove_fields` op will take the selected field out of
the edit and view topic panels, so that the field will be invisible for the user.

The `remove_fields` op accepts an array as argument with the labels
(or ids) of the individual fields to be removed.

```yaml
any_form:
    - remove_fields:
          - Reviewer
```

#### readonly_fields

The `readonly_fields` op will make one or more fields _readonly_, meaning the
user will be able to see it, but not change its value.

The `readonly_fields` op accepts an array as argument with the labels
(or ids) of the individual fields to be changed into readonly mode.

```yaml
any_form:
    - readonly_fields:
          - Reviewer
          - Assigned
```
