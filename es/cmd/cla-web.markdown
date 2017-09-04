---
title: cla web - Administración de servidores Web
index: 5000
icon: console
---

`cla web` arranca o detiene el servidor web de Clarive

## Opciones comunes

El subcomando `web` permite las siguientes opciones

`--env <entorno>` se utiliza para configurar los parámetros.

`--r` el servidor se reinicia automáticamente si hay algún cambio en las rutas:

- `CLARIVE_HOME/lib`
- `CLARIVE_HOME/conf`
- `features/\*/lib`, excepto si los cambios se detectan en ficheros de la ruta *features/#directorio* .

El valor por defecto es 0.

`--R <ruta>` El servidor se reinicia si hay algún cambio en la ruta indicada en `<ruta>`.

`--host <hostname>` Host o dirección IP para iniciar el servidor web. Si no se define, el host se coge de los archivos
de configuración.

`--port <portnum>` Puerto Web. Su valor por defecto es 3000.

`--daemon` Servidor Web se inicia como un demonio.

`--workers <workersnum>` Número de trabajadores para iniciar.

`--engine [Standalone|Twiggy|Starman|Starlet]` Servidor web PSGI. Su valor por defecto es Starman.

Si el servidor web se inicia en modo demonio, el log anterior será comprimido y se comienza a limpiar los procesos
*log*, los logs son borrados dependiendo del parámetro *log_keep* que se puede pasar como argumento para `cla web`.

`--log_keep <lognumber>` Número de logs que se pueden almacenar en la carpeta de logs.

`--log_file <logfile>` Nombre del fichero de log.

### web-start

Al igual que el `cla web` descrito anteriormente.

### web-stop

Detiene el servidor web. Este comando acepta los siguientes parámetros:

`no_wait_kill` - El dispatcher se elimina sin esperas. si está opción se está indicada, el dispatcher esperará 30
segundos antes de pararse.

`keep_pidfile` - Mantiene en el fichero el PID del proceso.

### web-restart

Reinicia el servidor web (señal ‘HUP’ 1).

`no_wait_kill` - El dispatcher se elimina sin esperas. si está opción se está indicada, el dispatcher esperará 30
segundos antes de pararse.

`keep_pidfile` - Mantiene en el fichero el PID del proceso.

### web-log

Imprime el fichero log en pantalla .

### web-tail

 Muestra el final del fichero log, acepta los siguientes argumentos:

`--tail [lineas]` - Número de lineas para mostrar. Por defecto muestra las últimas 500 líneas del log.

`interval [segundos]` - El número mínimo de segundos que va a esperar antes de que el fichero sea mostrado. Por defecto
es 0,5 segundos.

`maxinternal [segundos]` - El número máximo de segundos que el sistema esperará, por defecto es 1.
