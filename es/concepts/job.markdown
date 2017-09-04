---
title: Pase
index: 5000
icon: job
---

Los *trabajos*, *jobs* o *pases* son [reglas](/concepts/rule) ejecutadas por el servidor de Clarive.

Se ejecutarán siempre que estén planificados, si el usuario quiere ejecutar **ahora** un trabajo o en tres meses,
siempre se incluye en la planificador antes de que el [demonio](/admin/daemon) de trabajos lo ejecute.

Los trabajos pueden ser ejecutados las veces que se quiera a través de [reejecuciones](/concepts/rerun).

A diferencia de aplicaciones como *Jenkins*, los jobs no son planificados de forma estática por entidad. No puedes
planificar jobs de forma repetitiva. Los Jobs se *planifican una vez* y se *ejecutan una vez* (aunque de forma manual se
pueden replanificar y relanzar tantas veces como se quiera).

Si el usuario desea que un pase se ejecute de manera frecuente (por ejemplo, diariamente, cada dos días, mensual, etc.)
puede hacer uso del [planificador](/admin/scheduler).

Cuando se crea un pase, los pipelines disponibles serán los que tengan asociados los [proyectos](/concepts/project) de
los changesets que se quieran desplegar y que estén activos.

## Los pases son Recursos

El nombre del pase identifica al pase. Pero los pases, al igual que el resto de Recursos poseen un [MID](/concepts/mid)
con el que poder trabajar.
