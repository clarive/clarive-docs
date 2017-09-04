---
title: Menú de reglas
icon: rule
---

La ruta para acceder a las reglas es a través del menú de administración.

Seleccionando  **Admin - ![](/static/images/icons/rule.svg) Diseñador de Reglas** se abre una nueva pestaña con tres
áreas de trabajo diferentes.

### Área con el listado de reglas

- **Regla** - Muestra el id de la regla, el nombre y el tipo de regla.
- **Cuándo** - Muestra la fecha de la última modificación.

### Acciones

Las acciones que se pueden realizar son:

- ![](/static/images/icons/add.svg) **Crear** - Crear una nueva regla.
- ![](/static/images/icons/edit.svg) **Editar** - Edita la configuración general de la regla seleccionada.
- ![](/static/images/icons/delete.svg) **Borrar** - Elimina la regla seleccionada.
- ![](/static/images/icons/catalog-folder.svg) **Vista árbol** - Organiza las reglas basadas en su tipología.
- ![](/static/images/icons/restart-new.svg) **Activar/Desactivar** - Activa o desactiva la regla seleccionada.
- ![](/static/images/icons/exports.svg) **Herramientas** - ![](/static/images/icons/import.svg) Importa
  o ![](/static/images/icons/export.svg) Exporta la regla seleccionada en formato YAML para ser utilizado en otros
sistemas Clarive.

### Árbol de regla

Se trata del área donde se muestra la estructura de la regla como un árbol. En la barra de herramientas existen varias
opciones:

- ![](/static/images/icons/refresh.svg) **Refresca** - Actualiza la regla.
- ![](/static/images/icons/save.svg) **Guardar** - Guarda la regla.
- ![](/static/images/icons/ok.svg) **Validar** - Comprueba la regla (consulte [Análisis de
  calidad](/concepts/rule-quality-analysis)).
- ![](/static/images/icons/play.svg) **Ejecutar** - Se abre una nueva ventana con el [set de
  tests](/concepts/rule-test-sets) para que el usuario pueda realizar pruebas con el código DSL.
- ![](/static/images/icons/wrench.svg) **Herramientas** - Mas opciones acerca de la regla:
   - *Expresión regular* - Permite buscar por expresión regular.  - *Ignorar mayúsculas* - Permite realizar una búsqueda
     ignorando las mayúsculas.
   - *Historial* -  Busca la cadena deseada en todas las versiones de las reglas.
   - **Blame by time** - Marca los cambios en los elementos en un periodo específico de tiempo.
   - **Variables** - Muestra las [variables (Recursos)](/concepts/variable) que se utilizan en la regla.
   - ![](/static/images/icons/expandall.svg) **Expandir todo** - Expande todos los componentes de la regla.
   - ![](/static/images/icons/collapseall.svg) **Colapsa todo** - Colapsa todos los componentes de la regla.
   - ![](/static/images/icons/slot.svg) **Versión** - Expande toda el historial de versiones de la regla. Muestra las
fechas, la hora y el usuario que guardó la regla. Aquí existe la posibilidad de añadir etiquetas a una o varias de las
versiones anteriores de la regla, haciendo un clic derecho sobre la versión deseada y seleccionándose `Añadir etiqueta`.
Se introduce un nombre en el campo *Etiqueta*, lo que posibilita ejecutar una versión especifica de la regla a la hora
de [desplegar un Tópico](/getting-started/deploy-topics).
- ![](/static/images/icons/logo-html.svg) **HTML** - Muestra la regla en una página HTML.
- ![](/static/images/icons/workflow.svg) **Diagrama de flujo** - Muestra el árbol de la regla.

### Panel para la depuración de la regla

El panel de depuración ![](/static/images/icons/debug-view.svg) se muestra cuando se encuentra algún problema en la
regla. A través de este panel, se muestra en qué operación ocurre el problema y una breve descripción

### Paleta

Contiene todas las operaciones que pueden ser utilizadas para componer una regla.

Si el parámetro *show_in_palette* está inicializado a 1 en el fichero de configuración del elemento, la operación estará
disponible en la paleta.
