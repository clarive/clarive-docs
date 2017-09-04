---
title: cla disp - Gestión del Dispatcher
index: 5000
icon: console
---

Este comando inicia el Dispatcher Clarive.  El Dispatcher es el proceso encargado de iniciar y gestionar la
disponibilidad de todos los demonios activos. Para decidir qué demonios deben iniciarse, ya sea un fork o no, y otras
opciones, el Dispatcher utilizará las opciones de configuración de Demonios establecidas por el Administrador (consulte
Administración de Demonios para más información).

El Dispatcher maneja las señales recibidas y realiza la operación apropiada, cada segundo definido, comprobando el
estado de cada demonio activo. El comportamiento puede definirse como el siguiente:

- Si un demonio está activo en la lista de demonios, el dispatcher inicia el servicio.
- Si un demonio ha sido desactivado desde la herramienta, el dispatcher para el demonio.
- Si el demonio ha sido activado, el dispatcher arranca el servicio.
- Si un demonio está activo, el dispatcher comprueba si se está ejecutando o no, si no lo está intentará reiniciar el
  servicio de nuevo.

La frecuencia que el dispatcher comprueba el estado de un demonio es un parámetro configurable llamado `frecuency`. Este
valor, por defecto, son 30 segundos.


## Subcomandos

El comando `disp` acepta los siguientes subcomandos:

### disp-start

Igual que `cla disp`, inicia el dispatcher en modo online. Utilice `--daemon` para comenzar en segundo plano.

`--daemon`: ejecuta el servicio en segundo plano.

### disp-stop

Para el dispatcher y sus servicios. A su vez, este comando dispone de dos opciones más.

`no_wait_kill`: el dispatcher se elimina sin esperas. si está opción se está indicada, el dispatcher esperará 30 segundos antes de pararse.

`keep_pidfile`: mantiene en el fichero el PID del proceso.

### disp-log

Imprime el log en la pantalla.

### disp-tail

Muestra el final del fichero log, acepta los siguientes argumentos:

`tail`: número de lineas para mostrar. Por defecto muestra las últimas 500 líneas del log. Podemos modificar este número
ejecutando el comando: `cla disp-tail -tail=<numero-de-lineas>`.

`interval`: el número mínimo de segundos que va a esperar antes de que el fichero sea mostrado. Por defecto es 0,5
segundos.
