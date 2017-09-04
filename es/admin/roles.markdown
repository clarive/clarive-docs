---
title: Roles
index: 5000
icon: role
---

La seguridad de Clarive se gestiona a través del [sistema de roles](/concepts/roles).

Todos los accesos y funciones que puede desempeñar un usuario o administrador se definen a través de roles. Los usuarios
pueden tener uno o mas roles definidos. Esto hace que el acceso a Clarive por parte de un usuario esté limitado
y controlado.

**Ejemplo**

Un rol de administrador puede estar definido con todos los privilegios que puede tener un administrador estándar,
[administrador de categorías](/admin/categories), [administración de notificaciones](/admin/notifications), [acceso al
planificador](/admin/scheduler), [gestión de usuarios](/admin/user), etc...  Un gestor de incidencias puede estar
definido por ejemplo con acceso completo a la categoría Incidencia pero sin accesos a otros tópicos como 'Factura' que
podrá ser administrador por otro rol tipo "Jefe de RRHH".

Un usuario puede tener mas de un rol de tal manera que pueda acceder a más temas donde trabajar.

La administración de roles se realiza a través de la ruta Administración - ![](/static/images/icons/role.svg) Roles.
Esto mostrará un listado con todos los roles creados y una barra de acciones.

La lista contiene las siguientes columnas:

- `Rol` - El nombre del rol.
- `Descripción` - La descripción del rol.
- `Buzón` - Buzón al que pertenece el rol. Útil para las [notificaciones](/admin/notifications).
- `Opciones` - Resumen de las acciones del rol.


## Opciones de la lista de roles


### ![](/static/images/icons/add.svg) Crear

Pulsando en `Crear`, se abre una nueva ventana con las opciones necesarias para configurarlo:

- **Nombre del rol** - El nombre que define el rol, por ejemplo, *desarrollador*, *Release manager*, etc...
- **Descripción** - Una breve descripción del papel que desempeña el rol.
- **Dashboard** - Clarive dispone de un sistema de [dashboards](/concepts/dashboards). Aquí se pueden asociar los
  dashboards con roles de tal manera que en las [preferencias de usuario](/getting-started/prefs) solo aparecerán los
dashboards que estén asociados sus roles. El primer dashboard que se añada, será el dashboard por defecto. Cada usuario
podrá cambiar su dashboard por defecto en las preferencias del usuario.


### Acciones disponibles

Seleccione un usuario y haga click en `Editar`. Todas las acciones disponibles se muestran en el panel izquierdo, las
acciones al rol se muestran en el panel izquierdo.  Un grupo de acciones o una acción específica se pueden añadir
seleccionándola y arrastrando desde el panel izquierdo al panel derecho.

- `Descartar selección` ![](/static/images/icons/delete-grid-row.svg) - Elimina las acciones seleccionadas.
- `Descartar todas` ![](/static/images/icons/delete-grid-all-rows.svg) - Elimina todas las acciones asociadas
  al rol.

## Usuarios que tienen un rol

Permite ver los `Usuarios` que tienen el rol actual (en caso de estar en modo edición de rol) y en que
[ámbito](/concepts/scope) está asignado.

## Ámbitos que tiene usuarios con un rol asignado

Es una vista pivotal de la pestaña anterior. Permite ver los usuarios que tienen el rol.

## Acciones

Las acciones están agrupadas de manera lógica para una mejor localización de las mismas. Los grupos de acciones son los
siguientes:

- `---` - Acciones genéricas de usuario.
  - **Usuario puede cambiar su contraseña** `action.change_password`. El usuario puede cambiar su contraseña desde el
    menú de usuario.
  - **Ser un usuario diferente** `action.surrogate`. Permite al usuario acceder a la herramienta con otro usuario.
    Recomendado solo para administradores.
- `admin` - Todas las acciones relacionadas con la administración de la herramienta; administración de categorías,
  administración de usuarios, etc...
    - **Administrar variables de configuración** `admin.admin.config_list`. El usuario podrá configurar varias opciones
      de configuración de tiempo de ejecución. Se recomienda sólo para administradores.
    - **Administrar demonios** `action.admin.daemon`. El usuario puede ver, editar o administrar
      [demonios](/admin/daemon).
    - **Administrar eventos** `action.admin.event`. El usuario puede consultar todos los eventos que suceden en Clarive.
    - **Administrar etiquetas** `action.admin.labels`. El usuario puede crear, editar o administrar
      [etiquetas](/admin/labels).
    - **Administrar instantáneas** `action.admin.snapshots`. El usuario puede crear, eliminar o exportar
      [instántaneas](/admin/snapshot).
    - **Administrar notificaciones** `action.admin.notifications`. El usuario puede administrar el sistema de
      [notificaciones](/admin/notifications).
    - **Administrar roles** `action.admin.role`. Permite al usuario administrar los roles.
    - **Acción Root** `action.admin.root`. El usuario tendrá los mismos permisos que el usuario de sistema root.
      Recomendado solo para administradores del sistema. Use esta acción en vez de utilizar el usuario de sistema root.
De esta manera se podrá distinguir a los diferentes administradores.
    - **Administrar reglas** `action.admin.rules`. Permite al usuario ver y administrar las
      [reglas](/admin/rule-designer). Es posible utilizar este permiso solo para determinadas reglas.
    - **Administrar planificador** `action.admin.scheduler`. Permite al usuario administrar el
      [planificador](/admin/scheduler) para ejecutar reglas.
    - **Administrar semáforos** `action.admin.semaphore`. El usuario podrá ver y administrar los semáforos. Recomendado
      solo para administradores.
    - **Mensajes del sistema** `action.admin.sms`. El usuario podrá enviar [mensajes del sistema](/admin/system-messages)
     a todos los usuarios existentes en la herramienta.
    - **Administrar tópicos** `action.admin.topics`. Permite al usuario administrar las categorías de
     [tópicos](/concepts/topic).User will be able to admin topic categories. Recomendado solo para administradores.
    - **Actualizaciones** `action.admin.upgrade`. OBSOLETO
- `calendar` - Agrupan todas las acciones relacionadas con el calendario de pases.
    - **Administrar Calendarios de Pases** `action.calendar.admin`. El usuario podrá administrar las [ventanas de
      pases](/admin/calendaring).
    - **Editar Calendarios de Pases** `action.calendar.admin`. El usuario podrá solo editar las [ventanas de
      pases](/admin/calendaring) existentes.
    - **Ver Calendarios de Pases** `action.calendar.admin`. El usuario solo podrá ver los [calendarios de
      pases](/admin/calendaring).
- `catalog` - OBSOLETO
- `ci` - Todas las acciones relacionadas con los Recursos. Se pueden dar permisos para administrar o ver. El permiso
  administrar también da permisos para ver los Recursos por lo que no es necesario añadir los dos. Para especificar los
Recursos, hay que arrastrar la acción. En la ventana nueva, seleccionar los roles y las colecciones que el usuario puede
ver/administrar. Es posible añadir también filtros negativos. Por ejemplo, en caso de que el usuario pueda ver todos los
Recursos menos la colección Proyecto, se puede añadir Todos los roles y luego un filtro negativo para dicha colección.
- `dashboards` - Acciones relacionadas con los dashboards.
    - **Cambiar dashboard en desde el explorador** `action.dashboards.view`. Por defecto, el usuario solo puede ver los
      dashboard especificados en sus roles. Con esta acción podrá acceder a todos los dashboards existentes en Clarive
a través del explorador.
- `development` - Acciones relacionadas con el menú de Desarrollo.
    - **Vaciar Caché** `action.development.cache_clear`. El usuario puede eliminar todos los datos cacheados en la
      aplicación incluidos los grids. Recomendado solo para entornos de desarrollo.
    - **Referencias ExtJS API** `action.development.ext_api`. El usuario puede consultar la documentación de ExtJS.
    - **Ejemplos de ExtJS** `action.development.ext_examples`. El usuario puede acceder a ver ejemplo de uso de ExtJS.
    - **Diseñador GUI** `action.development.gui_designer`. OBSOLETO.
    - **Recargar JS** `action.development.js_reload`. El usuario será capaz de obligar a la aplicación a recargar todos
      los scripts del lado del cliente.
    - **REPL** `action.development.repl`. El usuario podrá ejecutar código arbitrario en el entorno de la aplicación.
      Recomendado sólo durante el desarrollo. **PELIGROSO**
    - **Secuencias** `action.development.sequences`. El usuario podrá ver secuencias de bases de datos.
- `git` - Acciones relacionadas con el repositorio Git.
    - **Usuario puede cerrar ramas** `action.git.close_branch`. El usuario será capaz de ignorar las ramas de
      repositorio desde el panel de ciclo de vida
    - **Acceder al repositorio git para pull/push** `action.git.repository_access`. El usuario podrá realizar pull
      y push al repositorio.
    - **Acceder al repositorio solo para pull** `action.git.repository_read`. El usuario podrá realizar pull del
      repostorio.
    - **Puede actualizar las etiquetas del sistema de repositorios** `action.git.update_tags`. El usuario podrá mover
      las etiquetas del sistema (entornos) en los repositorios.
- `help` - Acciones relacionadas con el menú de ayuda.
    - **Ver información del servidor en la ventana de Acerca de** `action.help.server_info`. El usuario podrá ver
      información más detallada en la ventana.
- `home` -  Acciones relacionadas con la herramienta como poder tener acceso al panel de ciclo de vida o al menú
  superior.
    - **El Usuario puede generar documentación desde los tópicos y vistas** `action.home.generate_docs`. OBSOLETO
    - **El Usuario puede acceder al menú** `action.home.show_menu`. El usuario puede ver el menú principal de la
      herramienta.
    - **El usuario puede acceder a los repostiorios de un proyecto** `action.home.view_project_repos`. El usuario puede
      ver los repositorios assignados a un proyecto desde el panel de ciclo de vida.
    - **El usuario puede acceder a las vistas de releases** `action.home.view_releases`. El usuario puede ver las
      releases desde el panel de ciclo de vida.
    - **El usuario puede acceder a la vista de workspace** `action.home.view_workspace`. OBSOLETO.
- `jobs` - Todo lo relacionado con despliegues, posibilidad de crear un nuevo [pase](/concepts/job), reiniciar un
  despligue, cancelarlo, etc...
    - **Acceder al menú avanzado en el detalle del log de pase** `action.job.advanced_menu`. El usuario puede acceder
      a los datos del stash. Recomendado solo para administradores.
    - **Aprobar/Rechazar un pase** `action.job.approve_all`. Permite al usuario aprobar o rechazar pases desde el
      [monitor](/admin/monitoring).
    - **Cancelar pases** `action.job.cancel`. Permite al usuario cancelar pases. Es posible asignar esta acción solo
      para determinados entornos.
    - **Cambiar la regla por defecto en la ventana de nuevo pase** `action.job.chain_change`. El usuario puede cambiar
      la regla de pase durante la creación de un nuevo pase. Recomendado solo para administradores.
    - **Cambiar el estado del pase en el paso POST** `action.job.change_step_status`. Permite al usuario cambiar el
      estado del pase en el paso POST. Es posible asignar esta acción a determinados entornos.
    - **Crear nuevos pases** `action.job.create`. Permite al usuario crear nuevos pases. Esto incluye cualquier tipo de
      pase.
    - **Eliminar un pase** `action.job.delete`. El usuario puede eliminar un pase. No es recomendable eliminar pases. Es
      posible asignar esta acción para determinados entornos.
    - **Forzar Rollback** `action.job.force_rollback`. El usuario puede forzar el rollback aunque no sea necesario. Es
      posible asignar esta acción a entornos concretos.
    - **Crear pases fuera de ventana** `action.job.no_cal`. El usuario podrá crear pases fuera de las [ventanas de
      pase](/admin/calendaring) disponibles.
   - **Reiniciar pases** `action.job.restart`. El usuario podrá reiniciar pases a través del Monitor. Es posible asignar
     esta acción a determinados entornos.
    - **Reanudar pases** `action.job.resume`. El usuario podrá reanudar pases a través del Monitor, por ejemplo desde el
      estado PAUSA.Es posible asignar esta acción a entornos específicos.
    - **Ejecutar pases In-Proc, sin Servidor Web** `action.job.run_in_proc`. El usuario podrá ejecutar los pases dentro
      del proceso del servidor web.  No es necesario que el dispatcher esté funcionando. Recomendado sólo durante el
desarrollo.
   - **Ver el Monitor de pases** `action.job.view_monitor`.El usuario podrá ver el Monitor de pases.
    - **Ver todos los pases** `action.job.viewall`. El usuario podrá ver los pases en el Monitor de pases.  Es posible
      asignarla sólo a un entorno específico.
- `labels` - Permite al usuario realizar acciones tales como añadir una etiqueta o eliminarla de un tópico.
    - **Adjuntar etiquetas a un tópico** `action.labels.attach_labels`. El usuario podrá adjuntar etiquetas a los
      tópicos.
    - **Eliminar etiquetas de un tópico** `action.labels.remove_labels`. El usuario podrá eliminar etiquetas de los
      tópicos.
- `projects` - Acciones relacionadas con el ciclo de vida de un proyecto.
    - **El usuario puede acceder a los proyectos desde el panel del ciclo de vida** `action.project.see_lc`. El usuario
      podrá ver los proyectos desde el panel de ciclo de vida.
- `report` - Acciones que permiten ver informes o ver los campos dinámicos de un informe.
    - **Ver campos dinámicos** `action.reports.dynamics`.El usuario podrá ver campos de informes dinámicos.
    - **Ver informes** `action.reports.view`. El usuario podrá acceder al menú de Informes desde el panel de ciclo de
      vida.
- `search` - Acciones que permiten al rol buscar jobs, Recursos o tópicos.
   - **Buscar CIs** `action.search.ci`. El usuario podrá buscar Recursos desde la barra de búsqueda situada en la parte
     superior de la herramienta.
    - **Buscar pases** `action.search.job`. El usuario podrá buscar pases desde la barra de búsqueda situada en la parte
      superior de la herramienta.
    - **Buscar tópicos** `action.search.topic`. El usuario podrá buscar tópicos desde la barra de búsqueda situada en la
      parte superior de la herramienta.
- `topics` - Permite al usuario ver tópicos, eliminar tópicos, crear un tópico, añadir comentarios en los tópicos,
  etc... Una vez que la acción es arrastrada, es posible filtrar para que el usuario solo pueda realizar dicha acción
para determinadas categorías.
    - **Ver actividad del tópico** `action.topics.activity`. El usuario podrá ver la actividad del tópico. Esto incluye
      todos los cambios en los datos de los tópico.
    - **Añadir/Ver los comentarios en los tópicos** `action.topics.comments`. Permite al usuario ver o añadir
      comentarios.
    - **Crear Tópico** `action.topics.create`. El usuario puede crear tópicos para todas o para categorías específicas.
    - **Eliminar tópico** `action.topics.delete`. El usuario puede eliminar tópicos para todas o para categorías
      específicas.
    - **Editar tópico** `action.topics.edit`. El usuario puede editar tópicos de todas o de las categorías específicas.
    - **Ver los pases del tópico** `action.topics.jobs`. El usuario puede ver los pases donde el tópico ha sido
      incluido.
    - **Cambiar el estado del tópico logicamente (sin pase)** `action.topics.logical_change_status`. El usuario podrá
      cambiar el estado de los tópicos sin iniciar un pase si así lo requiere el workflow del tópico.
    - **Ver tópico** `action.topics.view`. El usuario puede ver tópicos para todas o para categorías específicas.
    - **Ver gráfico de relaciones en el tópico** `action.topics.view_graph`.  El usuario puede ver las gráficas de las
      relaciones del tópico.
- `topicsfield` - Permite configurar las acciones para ver y/o editar los campos de los tópicos. Es posible
  configurarlos en función de la categoría y el estado del tópico. Tan solo hace falta añadir la categoría, el estado
y el campo para que el usuario pueda interactuar con el mismo. También es posible realizar filtros en negativo, por
ejemplo, dotar a un usuario de permisos para ver todos los campos de una categoría menos el campo 'Estimación'. Para
ello, se le asigna permisos para ver todos los campos de esa categoría y se le asigna un filtro negativo para el campo
'Estimación'.

### ![](/static/images/icons/edit.svg) Editar

Permite editar el rol seleccionado. Una vez realizados los cambios, seleccionar `Aceptar`. Si no desea guardar tras
editar un rol, seleccione `Cerrar`.

### ![](/static/images/icons/copy.svg) Duplicar

Permite duplicar el rol seleccionado. Se creará un nuevo rol con los mismos valores que el original. Es decir, mismas
acciones y dashboards así como la descripción. El nombre es el mismo pero con un número entero concatenado al final del
nombre.

### ![](/static/images/icons/delete.svg) Eliminar

Elimina uno o varios roles seleccionados. El sistema pedirá confirmación de ello antes de eliminarlo. Si se borrar un
rol que está asignado a un usuario, el rol también se eliminará del usuario.

Además, se dispone de una barra de búsqueda para buscar Roles por Rol o descripción.
