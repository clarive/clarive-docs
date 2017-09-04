---
title: Monitor
index: 5000
icon: television
---

El monitor muestra la lista de [pases](/concepts/job) que han sido creados y que el usuario puede ver en función de sus
permisos.  Se puede modificar la forma en la que se crean los nombres de los pases modificando la variable
*config.job.mask* [Configurar la máscara de pase](/how-to/config-job-mask).

Los siguientes botones se encuentran disponibles arriba de la lista de pases:

![](/static/images/icons/logo-html.svg) **HTML** - Muestra el log de el pase seleccionado en formato html.

![](/static/images/icons/project.svg) **Proyecto** - Filtra los pases por proyecto.

![](/static/images/icons/ci-bl.svg) **Entorno** - Filtra los pases por [entorno](/concepts/environment).

![](/static/images/icons/nature.svg) **Naturaleza** - Filtra los pases por naturaleza.

![](/static/images/icons/state.svg) **Estado** - Filtra los pases por estado.

**Tipo** - Filtra los pases por tipo.

![](/static/images/icons/job.svg) **Nuevo** - Crea un nuevo pase.

![](/static/images/icons/job-full-log.svg) **Log Completo** - Muestra el log de el pase seleccionado.

![](/static/images/icons/delete.svg) **Borrar** - Borra el pase seleccionado.

![](/static/images/icons/left.svg) **Rollback** - Ejecuta el [rollback del job](/concepts/rollback).

![](/static/images/icons/job-restart.svg) **Reiniciar** - Comienza el pase de nuevo desde el paso que el usuario desee.

![](/static/images/icons/datefield.svg) **Replanificar** - Modifica la planificación del pase. Esta acción sólo esta
disponible cuando el estado del job está en "Listo" o "Esperando Aprobación"
