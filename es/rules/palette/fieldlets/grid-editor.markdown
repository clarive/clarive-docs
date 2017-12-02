---
title: Editor de grids
index: 5000
icon: fieldlet-grid-editor
---

Permite añadir una tabla con las columnas personalizadas.

La lista de elementos que pueden ser configurados dentro del fieldlet.

### Ubicación del fieldlet

Indica en que parte de la vista se pondrá el fieldlet.

- **Cabecera** - Se muestra en la parte central del formulario.
- **Más información** - Se muestra en la pestaña de Más información situada en la parte inferior del tópico

### Anchura en canvas

Establece el ancho que ocupará el elemento en el formulario.

El valor máximo permitido es de 12 (100% de anchura de la pestaña).

### Altura en canvas

Establece el alto que ocupará el elemento en el **formulario de edición**.

El valor máximo permitido es de 12.

### Ocultar en el modo lectura

Indica si el campo se quiere ocultar en modo lectura.

### Ocultar en el modo edición

Indica si el campo se quiere ocultar en modo edición.

### Campo obligatorio

Indica si el campo tiene que ser completado obligatoriamente.

### Columnas

Establece los campos y el formato de la tabla.

Los nombres de las columnas van separados por ;

Después del nombre de la columna, hay que indicar el tipo de columna (si se omite, es un área de texto), o, en caso de
querer un menú desplegable, las opciones.

Ejemplo

    Sub-Tarea,textfield,250;Estado,combo_dbl,,Nuevo,Nuevo#En Progreso#Hecho;Fecha,datefield;Activo,cbox

Con este ejemplo se crean cuatro columnas, la primera llamada Sub-Tarea, de tipo texto y limitado a 250 caracteres.

A continuación se crea otra columna 'Estado', un combo desplegable (tipo combo_dbl) con la opción predeterminada al
principio y tras la coma y las opciones separadas por almohadilla.

La siguiente es una columna llamada Fecha de tipo fecha.

Por último creamos una columna de tipo checkbox que te permite elegir entre dos valores, activo e inactivo.

              Sub-Tarea  |  Estado  |    Fecha      |   Activo
           ------------------------------------------------------
            <area-texto> | <combo>  | <campo-fecha> | <checkbox>
