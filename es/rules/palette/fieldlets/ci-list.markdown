---
title: Lista de CIs
index: 5000
icon: fieldlet-ci-list
---

Permite añadir una lista de Recursos en el formulario.

La lista de elementos que pueden ser configurados dentro del fieldlet.

### Sección

Indica en que parte de la vista se pondrá el fieldlet.

- **Cabecera** - Se muestra en la parte central del formulario.
- **Más información** - Se muestra en la pestaña de Más información situada en la parte inferior del tópico.

### Ancho columna

Establece el ancho que ocupará el elemento en el formulario.

El valor máximo permitido es de 12 (100% de anchura de la pestaña).

### Altura en canvas

Establece el alto que ocupará el elemento en el **formulario de edición**.

El valor máximo permitido es de 12.

### Ocultar en el modo vista

Indica si el campo se quiere ocultar en modo lectura.

### Ocultar en el modo edición

Indica si el campo se quiere ocultar en modo edición.

### Campo obligatorio

Indica si el campo tiene que ser completado obligatoriamente.

### Tipo

Permite definir la apariencia de la tabla en el tópico:

- **Único** - Permite seleccionar unicamente una opción.
- **Múltiple** - Permite al usuario añadir tantas opciones como desee.
- **Tabla** - Las opciones seleccionadas se muestran en una tabla.

### Campo mostrado

En caso de no haber seleccionado el tipo Tabla en la opción anterior, se establece el texto para mostrar en la opción
seleccionada.

Por defecto, es el titulo lo que se muestra.

### Filtro avanzado JSON

Permite añadir un filtro avanzado JSON.

En este ejemplo solo mostrará un proyecto para mostrar:

        {"name":"Nombre_proyecto"}
        {"moniker":"Alias_del_proyecto"}

Los campos seleccionables para poder filtrar se pueden consultar a través del REPL. En este caso el comando será:
`ci->project->find_one();`

También es posible aplicar intervalos para limitar los resultados. Para ello es necesario hacer uso de los comandos *lt*
y *gt* propios de MongoDB.

Así para mostrar solo proyectos creados durante un intervalo de tiempo bastaria con construir la siguiente query:

        {"ts": {"$gt":"2016-03-22","$lt":"2016-04-08" } }


### Método de selección

Permite especificar los valores que salen en el formulario. Dos tipos a elegir:

- **Selección de rol** - Selecciona el rol a mostrar en el formulario, sin importar la clase. Si seleccionamos por
  ejemplo Agente, en el formulario se podrá seleccionar cualquier agente independientemente de si es *ftp_agent*,
*clax_agent*, etc...
- **Selección por clase** - Se habilita el campo Clase CI, donde una vez especificado el rol en el campo anterior,
  especificamos la clase (*ftp_agent*, *clax_agent*, etc...) y se mostraran solo los Recursos que pertenecen a la clase
indicada.

### Valor por defecto

Se selecciona el valor por defecto que se quiere por defecto en la lista.

Este campo estará habilitado cuando se seleccione una clase CI.

### Campo para filtrar

Permite filtrar la lista de los tópicos en función de un campo de este mismo formulario.

Este campo es obligatorio si el siguiente campo no está vacio.

### Datos para filtrar

Indica el campo por el que realizar el filtro.

Este campo es obligatorio si el campo anterior no está vacio.

### Tipo de filtro

Indica la lógica del filtro.

Por defecto, el tipo es OR.

Para más información, hay un *how-to* llamado [Filtros es fieldlets](/how-to/filter-fieldlet).


### Descripción

Selecciona la descripción que será mostrada al mostrar el listado de opciones.

- **Nombre** - Muestra el nombre del elemento.
- **Entorno** - Muestra los entornos separados por comas.
- **Clase** - Muestra el tipo de objeto que es.
- **Nemónico** - Muestra el nemónico especificado en la configuración del Recurso.


### Altura

Define la altura del grid en modo edición.
