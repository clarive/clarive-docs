---
title: Tablero Kanban de tópicos
index: 5000
icon: board
---

Clarive dispone de tableros Kanban los cuales están disponibles en dos escenarios:

- El grid de Tópicos.
- Dentro de un tópico que tiene dependencias con otros tópicos.

La tabla Kanban se abre pulsando el icono ![](/static/images/icons/board.svg)

### ¿Como funciona?

La tabla Kanban siempre comienza de una lista de tópicos, o del grid, o de tópicos relacionados entre sí. Si un tópico
no cuenta con ninguna dependencia con otro/s tópico/s, Kanban será accesible únicamente seleccionando el tópico en
cuestión dentro del grid.

De esa lista se generan las tablas donde muestran todos los estados disponibles en los que el tópico o los tópicos
puede/n estar (transiciones que se pueden ejecutar para los tópicos que se muestran).  Asímismo aparecen directamente
debajo los entornos correspondientes a aquellos estados.

Los estados para los que el usuario no tenga permiso a transitar o que no están disponibles como transición no se
mostrarán

Para cambiar el [estado](/concepts/status) de un tópico, basta con arrastrar y soltar al nuevo estado, con las excepción
de entornos promocionables (véase abajo). Se indica en cuáles estados se puede soltar el elemento arrastrado con un
cuadro de línea discontinua a su paso por encima de la columna del correspondiente estado. En caso de entornos no
promocionables, bastará soltar el tópico al nuevo estado sin lanzar un pase. Cuando un tópico esté colocado en otra
columna de Estado, éste será el nuevo estado del tópico.

## Barra de herramientas

**Modo selección**

Se puede hacer de dos maneras, buscando por la caja de búsqueda, donde los tópicos del listado que coincidan con el
patrón introducido quedarán marcados en color amarillo, o bien, haciendo click en activar selección manual, donde iremos
haciendo click sobre los tópicos que queremos seleccionar.

Un vez seleccionados, podremos hacer diferentes acciones sobre ellos:

- Borrar tópicos seleccionados.
- Borrar tópicos no seleccionados.
- Seleccionar todo.
- Deseleccionar todo.

**Añadir tópicos**

Nos permite añadir tópicos de cualquier categoria al tablero Kanban.

**Columnas**

Nos permite personalizar la vista del Kanban, pudiendo mostrar/ocultar estados, mostrar sólo tópicos, mostrar estados
con cambio de entornos, etc.

**Vistas**

Nos permite seleccionar el modo Footprint:

- FootPrint: Visualiza el historial del tópico con los cambios de estado y el tiempo que ha estado en tópico en cada
estado. El tiempo puede aparecer en tres colores diferentes, verde, amarillo o rojo. Estos colores son fijos, sin
embargo aparecen cuando el tópico lleva demasiado tiempo en un mismo estado. Para configurar en qué momento se debe
mostrar un tópico en amarillo o en rojo, es necesario acceder a la administración de [Categorías](/admin/categories)
y configurar la pestaña *SLA*.

**Guardar**

Nos permite guardar el Kanban con los cambios que hayamos personalizado. Podremos guardarlo, bien creando un Kanban
nuevo a partir del existente, bien sobrescribiendo el mismo.

**Expandir/Ajustar**

Nos permite expandir/ajustar el Kanban a la pantalla, pudiendo tener una mejor visualización del mismo.

**Resetear configuración**

Nos permite volver a la vista inicial, antes de haber aplicado algún cambio.

**Pantalla completa**

Nos permite ver el Kanban en pantalla completa.

**Cerrar Kanban**

Nos permite cerrar Kanban y volver a la pestaña anterior.

### Promocionar / Degradar a otros entornos

Para los estados que están vinculados a entornos, figura el nombre del entorno en la parte de arriba.

Si un tópico es arrastrado a un entorno promocionable, se abrirá una nueva ventana de pase.  En él se planificará el pase
nuevo y se ejecutará según el procedimiento estándar. Cuando se ejecute un pase, la cadena de proyecto se encargará de
desplegar el contenido del cambio y de promocinonarlos tópicos al correspondiente entorno de destino y correspondiente
estado (o de degradarlos de los mismos). Una vez finalizado con éxito, el tópico estará situado debajo del nuevo estado.

### Personalizar el tablero Kanban

El tablero se puede personalizar añadiendo o eliminando columnas (estados).

Estas personalizaciones se pueden guardar para futuros usos a través del botón `Guardar capas`.  Este botón solo está
habilitado cuando se accede al Kanban a través de un tópico. Esta opción no está disponible a tableros grid de tópicos.
