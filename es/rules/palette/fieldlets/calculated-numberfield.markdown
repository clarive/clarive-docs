---
title: Cálculo númerico
index: 5000
icon: fieldlet-calculated-number
---

Permite realizar una operación de cálculo recibiendo los valores a operar de fieldets de tipo
[numérico](/rules/palette/fieldlets/numberfield).

La lista de elementos que pueden ser configurados dentro del fieldlet.

### Ubicación del fieldlet

Indica en que parte de la vista se pondrá el fieldlet.

- **Cuerpo** - Se muestra en la parte derecha del formulario, debajo de la sección de detalles.

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

### Operación

Especifica, con los parámetros necesarios la operación matemática a realizar.

Ejemplos: $1 * $2, $1 + $2, $1 - $2...

### Campos de la operación

Se especifíca los campos que se van a utilizar en la operación.

Los campos, que son los IDs de los fieldlets de tipo numérico, van separados con comas.

Ejemplo: id1, id2 - Donde id1 y id2 indican dos fieldlets de tipo numérico creados anteriormente en la regla.

En este ejemplo, la variable $1 puesta en el campo Operación haría referencia a id1 y el $2 al id2.
