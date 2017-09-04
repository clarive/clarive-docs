---
title: Categorías
index: 5000
icon: topic
---

La administración de categorías se ubica dentro de las opciones de Administración - ![](/static/images/icons/topic.svg)
Categorías.

### Interfaz general

La lista contiene las siguientes columnas:

- `Casilla de verificación` - La casilla de verificación debe seleccionarse para que los botones de edición se
  habiliten. Tenga en cuenta que se pueden hacer varias selecciones, pero solo algunas de las opciones estarán
disponibles.
- `Categoría` - Indica el nombre de la Categoría y el color de la misma tal y como se mostrará en los tópicos.
- `ID` - Muestra el identificador único de cada categoría.
- `Acrónimo` - Indica el sobrenombre de la Categoría. Configurable dentro de las opciones de cada categoría.
- `Descripción` - Breve descripción de la Categoría.
- ` Tipo` - Indica el tipo de categoría.
    * *Normal* - Se trata de una categoría estándar, utilizado para las colaboraciones en un proceso de entrega
      continua.  Por ejemplo, son categorías de tipo normal Requerimientos, Incidencia, Tarea, Consulta, etc...
    * *Cambio* - Un tópico de esta categoría se utiliza para realizar un seguimiento de los cambios a nivel de código
      que forman parte del proceso.
    * *Release* - Esta categoría se utiliza para poder desplegar a otros entornos. Generalmente a los tópicos de tipo
      Release se asignan tópicos de una categoría de tipo Cambio para desplegar los nuevos cambios en el código en otros
entornos.

### ![Crear categoría](/static/images/icons/add.svg) Crear

Permite crear una nueva categoría.

Al pulsar en `Crear` se abre una nueva ventana con todas las opciones para crear una categoría a medida.

- `Categoría` - Campo de texto. Especifica el nombre de la nueva categoría.
- `Acrónimo` - Campo de texto. Indica el sobrenombre de la Categoría nueva.
- `Descripción` - Área de texto. Permite describir con más detalle la categoría, finalidad de la misma, uso, etc...
- `Tipo`- Indica el tipo de categoría. Ésta puede ser Cambio, Release o Normal.
- `Elije color` - Selecciona el color con el que se identificará a los tópicos.
- `Grid por defecto` - permite utilizar un informe como un grid personalizado.
- `Formulario`- Selecciona el [formulario](/rules/rule-concepts) con el que se completará la información de un tópico.
- `Dashboard` - Permite seleccionar un dashboard para ver la información en el tópico.
- `Proveedores` - Especifica el proveedor de la categoría. Éste puede ser creado de manera interna o se puede utilizar
  cualquiera de las integraciones permitidas por Clarive como Bugzilla, Basecamp, Trac, Redmine, BMC Remedy, Jira,
etc...
- `Opciones` - Permite crear tópicos de solo lectura. Usado en las integraciones para evitar sobrescribir información.
- `Lista de estados` - Permite seleccionar los [estados](/admin/status) que estarán disponibles en los tópicos de la
  categoría. Este grid muestra todos los estados disponibles y creados como Recursos y su descripción. Es importante
que las categorías tengan al menos un estado inicial y otro final.


### ![Borrar categoría](/static/images/icons/delete.svg) Borrar

Permite eliminar todas las categorías que están seleccionadas.

El sistema alertará de la acción y pedirá confirmación para seguir con el borrado evitando así borrados accidentales.

Las categorías no se puede eliminar si hay instancias de ésta en la base de datos. Estos casos deben ser revisados
primero y eliminados después antes de borrar la categoría. De esta manera se garantiza la integridad de la base de datos

### ![Editar categoría](/static/images/icons/edit.svg) Editar

Permite editar la categoría seleccionada. En modo Editar, aparece una nueva pestaña `Flujo de trabajo`. En ella se
especifica el flujo de estados que el tópico podrá transitar siempre en función de los roles.


### ![Duplicar categoría](/static/images/icons/copy.svg) Duplicar

Permite duplicar la categoría seleccionada. Esta opción solo está disponible cuando se ha seleccionado una categoria de
la tabla. Esta nueva categoría tendrá las mismas propiedades que la original. Solo va a tener diferente el nombre que
será el nombre de la categoría original seguido del ID generado para esta nueva categoría. Tras duplicar una categoría
es **recomendable** editarla y cambiar el nombre, descripción y demás elementos que pueden provocar confusión entre la
categoría original y la duplicada.

### ![Import_export](/static/images/icons/exports.svg) Importar/Exportar

El sistema permite importar y exportar las Categorias seleccionadas en caso de que querer copiar las categorías
existentes de un sistema a otro.

Al pulsar en ![Exportar](/static/images/icons/export.svg) Exportar, se abrirá una nueva ventana con el código
[YAML](/concepts/yaml) de las categorías seleccionadas.

Al pulsar en ![Importar](/static/images/icons/import.svg) Exportar, se abrirá una nueva ventana donde pegar el código
generado durante la exportación.

Una vez pulsado en `Importar` se podrá ver el progreso y estado de la importación en la parte inferior de la ventana.


### Editar el flijo de trabajo de la categoria seleccionada

Permite la edición de las restricciones del flujo de trabajo de la categoría seleccionada. Tenga en cuenta que esta
pestaña sólo está disponible cuando se ha seleccionado una categoría anteriormente guardada.

Las restricciones de flujo de trabajo están muy ajustadas a una función específica definida dentro Clarive.

Para crear una transición en función de un rol, primero se selecciona el rol y a continuación, en el menú desplegable,
el estado desde el cual comenzará la transición. Tras ello, aparecerá en la lista los estados de la categoría
disponibles y donde se elegirán los destinos de la transición. Para confirmar el flujo, pulsar
![](/static/images/icons/down.svg).

Para eliminar una transición, se selecciona la transición a borrar en la tabla inferior y se pulsa en
![](/static/images/icons/delete.svg) Borrar fila.

Para eliminar más de una transición de un rol especifico, se selecciona el rol en la lista de la izquierda y las
transiciones a la derecha. A continuación pulsar el botón de ![desasignar](/static/images/icons/clear-all.svg).
