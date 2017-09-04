---
title: Cla.ui - Configuración de formularios
index: 5000
icon: page
---

En Cla.ui. tienes todas las herramientas necesarias para la configuración de los formularios de nuevos CI o herramientas
a rellenar.

A continuación podrá ver todos los campos disponibles para añadir en los formularios.

## textField()

La opción Textfield le permite crear un campo para escribir algún texto.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **readOnly:** Pone el campo como solo lectura o editable. El valor for defecto es *false*.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.
- **anchor:** Define el ancho del campo.
- **height:** Define la altura del campo. Debe ser un valor numérico.
- **maxLength:** Define la longitud maxima que puede tomar el campo.
- **inputType:** Definirlo como 'password' si se está haciendo uso de este textField como contraseña.
- **style:** Define el estilo del campo.
- **enableKeyEvents:** Permite usar eventos para la entrada del campo HTML. El valor por defecto es *false*.

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

NumberField allows you to create a new field to place a numeric value. La opción numberField le permite crear un nuevo
campo para poner algún valor numérico.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **readOnly:** Pone el campo como solo lectura o editable. El valor for defecto es *false*.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.
- **anchor:** Define el ancho del campo.
- **height:** Define la altura del campo. Debe ser un valor numérico.
- **maxValue:** Define el máximo valor numérico que puedo tomar el campo.
- **maxLength:** Define la longitud maxima que puede tomar el campo.
- **style:** Define el estilo del campo.

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

La opción datetimeField muestra al usuario una fecha específica o le permite seleccionar una.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **readOnly:** Pone el campo como solo lectura o editable. El valor for defecto es *false*.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.
- **format:** Define el formato de fecha a mostrar.

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

La opción timeField muestra al usuario una hora específica o le permite seleccionar una.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **readOnly:** Pone el campo como solo lectura o editable. El valor for defecto es *false*.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.
- **format:** Define el formato de fecha a mostrar.

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

La opción textArea permite crear un campo de mayor tamaño para escribir algun texto.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **readOnly:** Pone el campo como solo lectura o editable. El valor for defecto es *false*.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.
- **anchor:** Define el ancho del campo.
- **height:** Define la altura del campo. Debe ser un valor numérico.
- **maxLength:** Define la longitud maxima que puede tomar el campo.
- **style:** Define el estilo del campo.

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

La opción comboBox permite crear un campo de seleccion con  diferentes opciones.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **data:** Define los valores predefinidos para el campo. El primer elemento será la clave que se enviará al controlador
del plugin. El segundo elemento es el valor que se verá en el desplegable del combo.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **disabled:** Deshabilita el campo.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.
- **anchor:** Define el ancho del campo.
- **width:** Define el ancho del campo con un valor numérico.
- **singleMode:** Define si se pueden escoger multiples opciones o solo uno a la vez. El valor por defecto es *false*.

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
            singleMode: true,
            comboDouble: true
        }),
    ]
})

```

## ciCombo()

La opción ciCombo le permite crear un campo de seleccion para escoger un CI específico.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **data:** Define los valores predefinidos para el campo.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **disabled:** Deshabilita el campo.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.
- **anchor:** Define el ancho del campo.
- **singleMode:** Define si se pueden escoger multiples opciones o solo uno a la vez. El valor por defecto es *false*.

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

La opción topicCombo permite crear un campo de seleccion para escoger un tópico en específico.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **disabled:** Deshabilita el campo.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.
- **anchor:** Define el ancho del campo.
- **singleMode:** Define si se pueden escoger multiples opciones o solo uno a la vez. El valor por defecto es *false*.
- **categories:** IDs de las categorías de tópicos que se desean mostrar. Deben estar en un array.
- **statuses:** IDs de los estados a mostrar. Deben estar en un array.
- **excludeStatus:** IDs de los estados a excluir en la lista. Deben estar en un array.

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

La opción codeEditor crea un campo para escribir codigo en un lenguaje determinado.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **anchor:** Define el ancho del campo.
- **height:** Define la altura del campo. Debe ser un valor numérico.
- **mode:** Define el lenguaje de programación para el editor.

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

La opción htmlEditor crea un campo para editar un documento html.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **readOnly:** Pone el campo como solo lectura o editable. El valor for defecto es *false*.
- **anchor:** Define el ancho del campo.
- **height:** Define la altura del campo. Debe ser un valor numérico.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.




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

## checkBox()

La opción checkBox crea una casilla de control.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **checked:** Sets an initial value.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **disabled:** Deshabilita el campo.

```javascript

(function(params) {
    return [
        Cla.ui.checkBox({
            name: 'check',
            fieldLabel: 'Check Box',
            checked: true,
            hidden: false,
            disabled: false
        })
    ]
})

```

## progressbar()

La opción progressbar crea un campo con una barra de progreso.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **disabled:** Deshabilita el campo.

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

La opción markdownEditor crea un campo para escribir un código markdown mostrando su previsualización.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **height:** Define la altura del campo. Debe ser un valor numérico.
- **hidden:** Pone el campo como oculto o no. El valor for defecto es *false*.
- **readOnly:** Pone el campo como solo lectura o editable. El valor for defecto es *false*.
- **anchor:** Define el ancho del campo.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.




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

La opción pill crea una caja de control con diferentes opciones.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **anchor:** Define el ancho del campo.
- **readOnly:** Pone el campo como solo lectura o editable. El valor for defecto es *false*.
- **options:** Define las opciones que se pueden seleccionar.

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

La opción projectCombo permite crear un campo de seleccion para elegir un proyecto.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **disabled:** Deshabilita el campo.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.
- **anchor:** Define el ancho del campo.
- **singleMode:** Define si se pueden escoger multiples opciones o solo uno a la vez. El valor por defecto es *false*.

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

La opción userCombo permite crear un campo de seleccion para elegir un usuario en específico.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **disabled:** Deshabilita el campo.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo. El valor for defecto es *true*.
- **anchor:** Define el ancho del campo.
- **singleMode:** Define si se pueden escoger multiples opciones o solo uno a la vez. El valor por defecto es *false*.

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

CategoryBox permite al usuario crear un cuadro de seleccion de una categoría de tópico.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **value:** Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **hidden:** Pone el campo como oculto o no. Falso por defecto.
- **allowBlank:** Permite que el campo quede sin rellenar u obliga a rellenarlo.
- **anchor:** Define el ancho del campo.
- **singleMode:** Define si se pueden escoger multiples opciones o solo uno a la vez.

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

DataEditor permite al usuario crear un editor de datos para crear estructuras hash y datos cone l metodo clave-valor.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **title:** Nombre del campo que se observará en la interfaz de usuario.
- **hide_save:** Esconde el botón de guardado.
- **hide_cancel:** Esconde el botón de cancelar.
- **hide_type:** Esconde la columna de seleccion de tipo de dato.
- **height:** Define la altura del campo. Debe ser un valor numérico.
- **data:**  Usted puede definir un valor por defecto mientras el usuario no lo cambie.
- **hidden:** Pone el campo como oculto o no. Falso por defecto.

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

Crea un campo para insertar expresiones regurales para el control de errores

Los parámetros para configurarlo son:

- **data:** Expresiones regulares para el control de errores.

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

Crea un panel donde se pueden tener más campos agrupados.

Los parámetros para configurarlo son:

- **layuot:** Selecciona el tipo de panel que es.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **frame:** Hace que el panel tenga una linea de separación visual.
- **hidden:** Pone el campo como oculto o no. Falso por defecto.
- **items:** Configura los diferentes campos del panel en un array.

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

Crea un panel donde puede escribir diferentes comandos, variables o frases en un array.

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **description:** Descripción del array.
- **value:** Selecciona un valor por defecto mientras el usuario no lo cambie.
- **default_value:** Valor por defecto cuando se le de a añadir una nueva linea.
- **hidden:** Pone el campo como oculto o no. Falso por defecto.

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

Los parámetros para configurarlo son:

- **name:** Es el nombre de la variable que cogerá el campo.
- **fieldlabel:** Nombre del campo que se observará en la interfaz de usuario.
- **width:** Define el ancho del campo. Debe ser un valor numérico
- **height:** Define la altura del campo. Debe ser un valor numérico.
- **columns:** Define el nombre de las columnas que habrá.
- **records:** Son los datos almacenados anteriormente.
- **hidden:** Pone el campo como oculto o no. Falso por defecto.
- **allowBlank:** Permite que el campo esté vacio u obliga a rellenarlo.

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

Trae los trés campos para el control de errores en ejecuciones remotas.

Los parámetros para configurarlo son:

- **errorTypeName:** Es el nombre de la variable que cogerá el campo para el tipo de error.
- **errorTypeValue:** Puede seleccionar un valor por defecto mientras el usuario para la selección del tipo de error.
- **rcOkName:** Es el nombre de la variable que cogerá el campo para el código de retorno rc Ok en el modo de control personalizado.
- **rcOkValue:** Puede seleccionar un valor por defecto mientras el usuario para el campo rc Ok en el modo personalizado.
- **rcWarnName:** Es el nombre de la variable que cogerá el campo para el código de retorno rc Warn en el modo de control personalizado.
- **rcWarnValue:** Puede seleccionar un valor por defecto mientras el usuario para el campo rc Warn en el modo personalizado.
- **rcErrorName:** Es el nombre de la variable que cogerá el campo para el código de retorno rc Error en el modo de control personalizado.
- **rcErrorValue:** Puede seleccionar un valor por defecto mientras el usuario para el campo rc Error en el modo personalizado.
- **errorTabsValue:** Almacena las expresiones regulares para e control de errores.

```javascript

(function(params) {
    return [
        Cla.ui.errorManagementBox({
            errorTypeName: 'tipo',
            errorTypeValue: params.data.tipo || 'warn',
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
