---
title: Opciones comunes en la linea de comandos
index: 3000
icon: console
---

Aquí se describen las opciones más comunes que soporta el comando de línea.

Algunos comandos no se pueden usar internamente, por lo que no se aplica necesariamente a todos los comandos, pero se
cargan a través del gestor de comandos principal de Clarive `cla`.

### -c [config_file]

Esta opción establece el fichero de configuración del fichero de configuración
(también llamado *entorno*) que va a ser utilizado. Por ejemplo, si utilizamos
la opción `-c mypersonal`, `cla` cargará las opciones de configuración que
estén dentro del fichero `config/mypersonal.yml`.

Antes esta opción se denominaba `--env` pero ha sido _deprecada_ en favor del `-c`
para mejor adherir a los estándares. La opción `--env` sigue soportada por motivos de
compatibilidad hacia atrás.

### --enable-plugins

Indica a Clarive si debe cargar los plugins en el arranque.

Use `--no-enable-plugins` para evitar que Clarive cargue los plugins alojados en el directorio `init/` al inicio.

### --debug

Activa el modo debug y reporta los mensajes debug al fichero de log.

### --trace [n]

Establece el nivel de seguimiento para mensajes de depuración.

### --base [path]

Establece una variable de entorno diferente a `CLARIVE_BASE`.

Ajustándola de esta manera, sobrescribe la establecida como variable de entorno.

### --home [path]

Establece una variable de entorno diferente a `CLARIVE_HOME`.

Por defecto, `CLARIVE_HOME` se establece en `CLARIVE_BASE/clarive`.

Ajustándola de esta manera, sobrescribe la establecida como variable de entorno.

## Opciones del fichero de configuración [env].yml

Todas las opciones aquí se pueden configurar también en el archivo `[config_file].yml`,
excepto la opción `-c` por razones lógicas.

Por ejemplo, esto podría ser un archivo `[env].yml`.
Todas las opciones con el guión `-` en el nombre, necesitan ser sustituidos por el guión bajo `_`:

```yaml
debug: 1
trace: 2
load_plugins: 0
```
