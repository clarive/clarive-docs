---
title: Despliegue de tópicos
index: 5000
icon: job
---

A la hora de desplegar un tópico en Clarive, su Estado deberá estar establecido en uno definido como desplegable en el
[flujo de trabajo](/concepts/workflow) de la Categoría correspondiente. Además el Tópico debe estar asociado con un
[Proyecto](/concepts/project).

Haga clic en `Nuevo Pase` y seleccione la Transición deseada.

Selecciona del combo *Cadena* la Regla tipo Cadena de pase que desea utilizar para el despliegue del Tópico.

El combo *Versión* da la opción de seleccionar la última versión de la Regla Cadena de pase, además de una o varias
versiones de la misma en el caso de haberse etiquetada versiones anteriores (véase [Menú de reglas](/rules/rule-menu)).

Cada versión etiquetada muestra el nombre introducido en su etiqueta, seguido por el usuario entre paréntesis, lo cual
ofrece la posibilidad de ejecutar una versión anterior de la regla.

Al seleccionar una versión de la regla que no es la última, aparecerá el campo *Etiquetas dinámicas*, esto
detecta la versión de la regla etiquetada más recientemente (en caso de que se haya movido). Si no está marcado, retiene la
primera versión de la etiqueta y ejecuta la versión de la regla correspondiente.

*Cuándo* nos permite seleccionar la Fecha y la Hora de despliegue, así consultando el [Calendario de
Pases](/guide/calendaring) para identificar una ranura disponible.

Es posible lanzar el pase sin tener en cuenta el calendario activando la opción *Chequee si quiere crear un pase fuera
de ventana*. Para ello, es obligatorio informar en el campo *Comentarios* un motivo.

El cuadro *Elementos de Pase* contiene los elementos del pase que van ser desplegados asi como las dependencias del pase.

Haga clic en `Crear` para crear el Pase. El seguimiento de éste se puede realizar desde el [Monitor](/getting-started/monitor).
