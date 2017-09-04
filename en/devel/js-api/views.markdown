---
title: Cla.ui - Forms configuration
index: 5000
icon: page
---

In Cla.ui. you have the necessary tools to configurate all the parameters to add in the forms to use in Clarive.

Bellow you will see all the available fields that you can add into the form.

## textField()

Textfield option allows you to create a new field to place some text.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **readOnly:** Sets the field to be readOnly or editable. Default value is *false*.
- **hidden:** Sets the field to be hidden or not. Default Value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.
- **anchor:** Sets the field width.
- **height:** Sets the field height. Must be a numeric value.
- **maxLength:** Sets the maximum length the field can have.
- **inputType:** Define it as 'password' if you are using it as a password textfield.
- **style:** Defines field styles.
- **enableKeyEvents:** Allow to use key events for the HTML input field. Default value is *false*.

```javascript

(function(params) {
    return [
        Cla.ui.textField({
            name: 'name',
            fieldLabel: 'Hello World Label',
            value: 'HelloWorld',
            readOnly: true,
            anchor: '50%',
            height: 20,
            maxLength: '10'
        })
    ]
})

```

## numberField()

NumberField allows you to create a new field to place a numeric value.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **readOnly:** Sets the field to be readOnly or editable. Default value is *false*.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.
- **anchor:** Sets the field width.
- **height:** Sets the field height. Must be a numeric value.
- **maxValue:** Sets the maximum value.
- **maxLength:** Sets the maximum length the field can have.
- **style:** Defines field styles.

```javascript

(function(params) {
    return [
        Cla.ui.numberField({
            name: 'number',
            fieldLabel: 'Number Field',
            value: '234',
            allowBlank: false,
            anchor: '50%',
            height: 20,
            maxValue: '1200'
        })
    ]
})

```

## datetimeField()

DatetimeField shows the user an specific date or allows to choose one.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **readOnly:** Sets the field to be readOnly or editable. Default value is *false*.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.
- **format:** Defines the format for the date to be showed.

```javascript

(function(params) {
    return [
        Cla.ui.datetimeField({
            name: 'date',
            fieldLabel: 'Date Time',
            value: '24/05/15',
            readOnly: true,
            allowBlank: false,
            format: 'd/m/y'
        })
    ]
})

```

## timeField()

TimeField shows the user an specific hour or allows to choose it.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **readOnly:** Sets the field to be readOnly or editable. Default value is *false*.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.
- **format:** Defines the format for the time to be showed.

```javascript

(function(params) {
    return [
        Cla.ui.timeField({
            name: 'time',
            fieldLabel: 'Time Field',
            value: '16:34',
            readOnly: true,
            hidden: true
        })
    ]
})

```

## textArea()

TextArea option allows you to create a bigger box to place a text.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **readOnly:** Sets the field to be readOnly or editable. Default value is *false*.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.
- **anchor:** Sets the area width.
- **height:** Sets the area height. Must be a numeric value.
- **maxLength:** Sets the maximum length the field can have.
- **style:** Defines field styles.

```javascript

(function(params) {
    return [
        Cla.ui.textArea({
            name: 'text',
            fieldLabel: 'Hello World Label',
            value: 'HelloWorld',
            readOnly: false,
            hidden: false,
            allowBlank: false,
            anchor: '50%',
            height: 50,
            maxLength: '10'
        })
    ]
})

```

## comboBox()

ComboBox allows to create a box with different options to select.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **data:** Defines the predefined values for the box. The first parameter will be the key that will be sent to the
plugin handler. The second parameter is the value you will see in the combo dropdown.
- **value:** You can set a default value while the user does not change it.
- **disabled:** Disables the field. Default Value is *false*.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.
- **anchor:** Sets the box width.
- **width:** Sets the box width with a numeric value.
- **singleMode:** Sets the combo box to be one option at the same time or more. Default value is *false*.

```javascript

(function(params) {
    return [
        Cla.ui.comboBox({
            name: 'combo',
            fieldLabel: 'Combo Box',
            data: [
                ['Data A', 'Option 1'],
                ['Data B', 'Option 2'],
                ['Data C', 'Option 3']
            ],
            value: 'Option 1',
            disabled: false,
            hidden: false,
            allowBlank: false,
            anchor: '100%',
            singleMode: true
        }),
    ]
})

```

## ciCombo()

CiCombo allows to create a box to choose an specific CI.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **class:** Defines the CI class to choose from.
- **disabled:** Disables the field. Default Value is *false*.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.
- **anchor:** Sets the field width.
- **singleMode:** Sets the combo box to be one option at the same time or more. Default value is *false*.


```javascript

(function(params) {
    return [
        Cla.ui.ciCombo({
            name: 'repo',
            class: 'generic_server',
            fieldLabel: 'CI Combo',
            allowBlank: false,
            anchor: '100%',
            singleMode: true
        })
    ]
})

```

## topicCombo()

TopicCombo allows to create a box to choose an specific topic.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **disabled:** Disables the field. Default Value is *false*.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.
- **anchor:** Sets the field width.
- **singleMode:** Sets the combo box to be one option at the same time or more. Default value is *false*.
- **categories:** Categories ID to be displayed. They must be into an array.
- **statuses:** Statuses ID to be displayed. They must be into an array.
- **excludeStatus:** Statuses ID to be excluded. They must be into an array.

```javascript

(function(params) {
    return [
        Cla.ui.topicCombo({
            name: 'topic',
            categories: ['21'],
            statuses: ['11'],
            fieldLabel: 'Topic Combo',
            allowBlank: false
        })
    ]
})

```

## codeEditor()

CodeEditor creates an area to write an specific code to be used later.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **anchor:** Sets field width.
- **height:** Sets field height. Must be a numeric value.
- **mode:** Sets the languaje mode for the editor.

```javascript

(function(params) {
    return [
        Cla.ui.codeEditor({
            name: 'code',
            fieldLabel: 'Code Editor',
            mode: 'Perl',
            height: 100,
            anchor: '100%'
        })
    ]
})

```

## htmlEditor()

HtmlEditor create an area to edit and html documento to be used later

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **readOnly:** Sets field to be readOnly or editable. Default value is *false*.
- **anchor:** Sets field width.
- **height:** Sets field height. Must be a numeric value.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.

```javascript

(function(params) {
    return [
        Cla.ui.htmlEditor({
            name: 'html',
            fieldLabel: 'Html Editor',
            height: 100,
            value: '<b>hola</b>',
            anchor: '100%'
        })
    ]
})

```

## checkBox()

CheckBox creates a check Box.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **checked:** Sets an initial value.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **disabled:** Disables the field. Default Value is *false*.

```javascript

(function(params) {
    return [
        Cla.ui.checkBox({
            name: 'check',
            fieldLabel: 'Check Box',
            checked: true,
            disabled: true
        })
    ]
})

```

## progressbar()

Progressbar creates a progress bar.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **disabled:** Disables the field. Default Value is *false*.

```javascript

(function(params) {
    return [
        Cla.ui.progressbar({
            name: 'bar',
            fieldLabel: 'Progress Bar',
            value: '50',
            hidden: false,
            disabled: false
        })
    ]
})

```

## markdownEditor()

MarkdownEditor creates an area to write some information in markdown format with its preview.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **height:** Sets field height. Must be a numeric value.
- **hidden:** Sets the field to be hidden or not. Default value is *false*.
- **anchor:** Sets field width.
- **readOnly:** Sets field to be readOnly or editable. Default value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.

```javascript

(function(params) {
    return [
        Cla.ui.markdownEditor({
            name: 'markdown',
            fieldLabel: 'Markdown Editor',
            height: 200,
            value: '',
            anchor: '100%',
            allowBlank: true
        })
    ]
})

```

## pill()

Pill creates a checkbox with different items to select one of them.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **anchor:** Sets field width.
- **readOnly:** Sets field to be readOnly or editable. Default value is *false*.
- **options:** Sets the different options to choose.

```javascript

(function(params) {
    return [
        Cla.ui.pill({
            name: 'pill',
            fieldLabel: 'Pill box',
            value: '',
            anchor: '100%',
            readOnly: false,
            options: ['A', 'B', 'C']
        })
    ]
})

```

## projectCombo()

ProjectCombo allows to create a box to choose an specific project.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **disabled:** Disables the field. Default Value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.
- **anchor:** Sets the field width.
- **singleMode:** Sets the combo box to be one option at the same time or more. Default value is *false*.


```javascript

(function(params) {
    return [
        Cla.ui.projectCombo({
            name: 'ProjectCombo',
            fieldLabel: 'Project Combo',
            allowBlank: true,
            disabled: false,
            anchor: '100%',
            singleMode: false
        })
    ]
})

```

## userCombo()

UserCombo allows to create a box to choose an specific user.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **disabled:** Disables the field. Default Value is *false*.
- **allowBlank:** Allows the field to be empty or force it to be filled. Default value is *true*.
- **anchor:** Sets the field width.
- **singleMode:** Sets the combo box to be one option at the same time or more. Default value is *false*.


```javascript

(function(params) {
    return [
        Cla.ui.userCombo({
            name: 'userCombo',
            fieldLabel: 'User Combo',
            allowBlank: true,
            disabled: false,
            anchor: '100%',
            singleMode: false
        })
    ]
})

```

## categoryBox()

CategoryBox allows to create a box to choose a topic category.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldlabel:** The name the box will have in the user interface.
- **value:** You can set a default value while the user does not change it.
- **hidden:** Sets the field to be hidden or not. False by default.
- **allowBlank:** Allows the field to be empty or force it to be filled.
- **anchor:** Sets the field width.
- **singleMode:** Sets the combo box to be one option at the same time or more.

```javascript

(function(params) {
    return [
        Cla.ui.categoryBox({
            name: 'categoryBox',
            fieldLabel: _('Category Box'),
            value: params.data.categoryBox || '',
            allowBlank: false,
            singleMode: true,
            anchor:'50%',
            hidden: false
        })
    ]
})

```

## dataEditor()

DataEditor allows to create a data editor to create hashes and key-value data.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **title:** The name the box will have in the user interface.
- **hide_save:** Hides save button from the box.
- **hide_cancel:** Hides cancel button from the box.
- **hide_type:** Hides save type column from the box.
- **height:** Sets the field height. Must be a numeric value.
- **data:** You can set a default value while the user does not change it.
- **hidden:** Sets the field to be hidden or not. False by default.

```javascript

(function(params) {
    return [
        Cla.ui.dataEditor({
            name: 'dataEditor',
            title: _('Data editor'),
            hide_save: true,
            hide_cancel: true,
            hide_type: true,
            height: 500,
            data: params.data.dataEditor ||
              {
                'title' : 'title',
                'description': 'description',
                'status' : 'name_status'
              }
        })
    ]
})

```

## errorOutputTabs()

Creates a field to set some regular expressions to control errors.

The parameters to configure it are:

- **data:** Regular expressions for error control.


```javascript

(function(params) {
    return [
        Cla.ui.errorOutputTabs({
            data: params.data
        })
    ]
})

```

## panel()

Creates a panel where you can have more fields together.

The parameters to configure it are:

- **layuot:** Sets the layuot for the panel.
- **fieldLabel:** The name the box will have in the user interface.
- **frame:** Set the field to have a visual separation line.
- **hidden:** Sets the field to be hidden or not. False by default.
- **items:** Configure the different fields inside the panel into an array.

```javascript

(function(params) {
    return [
        Cla.ui.panel({
        layout: 'column',
        fieldLabel: _('General panel'),
        frame: true,
        hidden: false,
        items: [{
            layout: 'form',
            columnWidth: .33,
            labelAlign: 'top',
            frame: true,
            items: {
                xtype: 'textfield',
                anchor: '100%',
                fieldLabel: _('Item 1'),
                name: 'item1',
                value: 'Item 1'
            }
        }, {
            layout: 'form',
            columnWidth: .33,
            labelAlign: 'top',
            frame: true,
            items: {
                xtype: 'textfield',
                anchor: '100%',
                fieldLabel: _('Item 2'),
                name: 'item2',
                value: 'Item 2'
            }
        }]
        })
    ]
})

```

## arrayGrid()

Creates a panel where you can write different commands, variables, or sentences into an array.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldLabel:** The name the box will have in the user interface.
- **description:** Set the description for the array.
- **value:** You can set a default value while the user does not change it.
- **default_value:** Sets the default value when the user want to add another line.
- **hidden:** Sets the field to be hidden or not. False by default.

```javascript

(function(params) {
    return [
        Cla.ui.dataEditor({
            fieldLabel: _('Array'),
            name: 'arrayGrid',
            value: 'test array',
            description: 'Array grid',
            default_value: '.',
            hidden: true
        })
    ]
})

```

## gridEditor()

Creates a field with the columns you set to be filled.

The parameters to configure it are:

- **name:** It is the variable name which the field will get.
- **fieldLabel:** The name the box will have in the user interface.
- **width:** Sets the field width.
- **height:** Sets the field height. Must be a numeric value.
- **columns:** Define the column names there will be.
- **records:** It is the stored data before.
- **hidden:** Sets the field to be hidden or not. False by default.
- **allowBlank:** Allows the field to be empty or force it to be filled.

```javascript

(function(params) {
    return [
        Cla.ui.dataEditor({
            fieldLabel: _("Grid Editor"),
            width: '100%',
            height: 300,
            name: 'gridEditor',
            columns: ['column1', 'column2'],
            records: data.params.gridEditor,
            allowBlank: true
        })
    ]
})

```

## errorManagementBox()

Brings three fields for error control in remote command launches.

The parameters to configure it are:

- **errorTypeName:** It is the variable name which the field will get for the error type.
- **errorTypeValue:** You can set a default value while the user does not change it for the error selection.
- **rcOkName:** It is the variable name which the field will get for the  rc Ok value in custom error mode.
- **rcOkValue:** You can set a default value while the user does not change it for the rc Ok value in custom error mode.
- **rcWarnName:** It is the variable name which the field will get for the rc Warn value in custom error mode.
- **rcWarnValue:** You can set a default value while the user does not change it for the rc Warn value in custom error mode.
- **rcErrorName:** It is the variable name which the field will get for the rc Error value in custom error mode.
- **rcErrorValue:** You can set a default value while the user does not change it for the rc Error value in custom error mode.
- **errorTabsValue:** Here you can writhe the regular expressions for the error control.

```javascript

(function(params) {
    return [
        Cla.ui.errorManagementBox({
            errorTypeName: 'type',
            errorTypeValue: params.data.type || 'warn',
            rcOkName: 'ok',
            rcOkValue: params.data.ok,
            rcWarnName: 'warn',
            rcWarnValue: params.data.warn,
            rcErrorName: 'error',
            rcErrorValue: params.data.error,
            errorTabsValue: params.data
    ]
})

```
