---
title: Tablas de Recursos
index: 5000
icon: class
---

Los [Recursos](/concepts/resource) representan una faceta fundamental de la configuración dentro de Clarive, pudiendo
ser gestionados los mismos a través de Tablas, las cuales consisten en listas de elementos de un determinado tipo
visibles al Usuario.

Se puede acceder a las Tablas seleccionando la opción de menú `Todos` del menú de Recursos, luego el tipo de elemento.
Además de poder ser seleccionados directamente desde el menú, también se agrupan tipos de elementos específicos bajo
nodos más genéricos del menú, p.ej. Entorno aparece por su cuenta, además de venir plasmado bajo `Interno`.

Otros ejemplos de Recursos abarcan servidores, User IDs, agentes, middleware (por ejemplo, JBoss o Apache), instancias
en la nube, nodos mainframe etc.

### Ordenación

Por defecto, la lista aparece ordenada por Fecha-Hora, del más antiguo al elemento más reciente.

Se puede cambiar la ordenación pinchando en el encabezado de la columna por la que se quiere ordenar la lista.  Con cada
click, se cambiará el tipo de ordenación (ascendiente/descendiente).

### Búsquedas

En una Tabla de Recursos tambien se puede buscar resultados utilizando el [buscador](/getting-started/search-syntax).

#### Crear

Se pueden crear Recursos directamente en la Tabla correspondiente haciendo clic en el botón `Crear` de la barra de
acciones, lo cual abre una pestaña de modo creación que contiene más opciones pata visualizar, modificar y borrar aquel
elemento individual.

#### Modificar

Se pueden hacer modificaciones haciendo clic en un elemento de la lista de la Tabla, lo que abre el mismo en una pestaña
modo modificación, conteniendo éste opciones parecidas a aquellas del modo creación.

#### Borrar

Mediante el botón `Borrar` se puede eliminar el/los elemento/s seleccionado/s.

#### Exportar

Clarive permite al Usuario la exportación de la Tabla en los formatos YAML, JSON, HTML y CSV mediante el botón
`Exportar` de la barra de acciones.

#### Importar

Asímismo el Usuario puede importar la Tabla respectivo en los formatos YAML y CSV mediante el botón `Importar` de la
barra de acciones.

#### Servicios de la clase

El botón `Servicios de la clase` abre un menú desplegable desde el cual se puede seleccionar un servicio personalizado
para la ejecución de instancias simultáneas del mismo tipo.

Esto podría consistir -a modo de ejemplo- en una ventana que contenga una serie de funciones, p.ej. botones para la
ejecución del servicio, pestañas, paneles de salida etc., dependiendo del tipo de elemento de que se trate.

#### Mostrar Gráfico

El botón `Mostrar Gráfico` abre una pestaña en que se muestran el/los elemento/s en una variedad de formatos de
[gráfico](/concepts/ci-graph) con relación a otros Recursos, p.ej. Proyectos o Usuarios.
