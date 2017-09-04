---
title: cla/reg - Manipulación del registro
index: 5000
icon: page
---

El registro Clarive sostiene los puntos de extensión en muchas partes del el sistema, tanto el cliente como el servidor.

Estas funciones son sobretodo útiles en `init/`, puntos de entrada de plug-in para registrar cosas como las operaciones
de la paleta (servicios), las entradas de menú, eventos y demás.

### cla.register()

Crea una entrada de registro en Clarive.

En el siguiente ejemplo, se crea una nueva entrada en el menú.

```javascript
var reg = require('cla/reg');
reg.register('menu.admin.test',{ name: 'Test Menu', url: '/comp/testmenu.js' });
```

### cla.launch(clave,opcs)

Lanza un servicio de registro.

```javascript
var reg = require('cla/reg');
reg.register('service.test',{
    name: 'Foo Service',
    handler: function(){ return 99 }
});

reg.launch('service.test', { name: 'just trying this out', config: { foo: 'bar' } });
```

Opciones:

- `config` - Un objeto de configuración que se enviará al controlador.
- `name` - Informa el nombre de la operación para que quede la información de registro es más descriptivo.
- `dataKey` - Informa el nombre de la operación para que quede la información capturada en el log sea más descriptiva.
- `stash` - Un *stash* alternativo; por defecto es el *stash* actual.

### Ejemplos de ejecución de servicios.

Para realizar la ejecución de servicios dentro de los plugins, es necesario conocer las variables que se le deben pasar
para el correcto funcionamiento del mismo.

Cualquier elemento de la paleta puede ser invocado desde un plugin, y de este modo tenerlo todo de una forma más
compacta.

Algunos de los elementos a los que se puede invocar son: Lanzamiento de scripts remotos, envío de archivos por SSH,
creación de tópicos, etc...

A continuación, se ponen algunos ejemplos de elementos de la paleta para invocar y las variables necesarias para estos.
No todas las variables son siempre necesarias, pero se exponen todas las que son posibles de utilizar.

### Ejecución de comandos remotos (service.scripting.remote)

Este servicio es el encargado de realizar ejecuciones de comandos de manera remota.

```javascript
reg.launch('service.scripting.remote', {
    name: 'Remote launch', // Nombre de la tarea a ejecutar
    config: {
        errors: 'fail', // Tipo de errores que se van a controlar
        server: '1234', // ID del servidor en el que se va a ejecutar
        user: 'clarive', // Usuario para conectar al servidor
        path: 'ls -l', // Comando que se quiere lanzar
        output_error: '', // Expresiones regulares para el control de errores
        output_warn: '', // Expresiones regulares para el control de errores
        output_capture: '', // Expresiones regulares para el control de errores
        output_ok: '', // Expresiones regulares para el control de errores
        meta: {foor: bar}, // Los metadatos del servicio donde se ejecuta
        rc_ok: '200', // Codigo de rc Ok para control de errores
        rc_error: '404', // Codigo de rc Error para control de errores
        rc_warn: '302' // Codigo de rc Warn para control de errores
    }
});
```

### Envío de archivos remoto (service.fileman.ship)

Servicio encargado de realizar el envío de archivos remotamente a otro servidor.

```javascript
reg.launch('service.fileman.ship', {
    name: 'Remote ship', // Nombre de la tarea a ejecutar
    config: {
        server: '1234', // ID del servidor al que se quiere enviar el archivo
        user: 'clarive', // Usuario para conectar al servidor
        recursive: "0", // Realizar la operación de manera recursiva o no
        local_mode: "local_files", // Modo de envío de archivos locales
        local_path: "Home/", // Ruta al archivo que se quiere enviar
        remote_path: "tmp/", // Directorio del servidor remoto donde quieres enviar el archivo
        exist_mode_local: "skip", // Modo de actuación ante archivos que no encuentre
        rel_path: "file_only", // Modo de envio, solo de archivos, o manteniendo la ruta del job
        exist_mode: "reship", // Modo de actuación ante archivos ya enviados por el job
        backup_mode: "none", // Modo de backup de archivos
        rollback_mode: "none", // Modo de rollback
        track_mode: "none", // Modo de seguimiento de archivos
        audit_tracked: "none", // Modo de auditoria de archivos
        chown: "", // Permisos de chown
        chmod: "", // Permisos de chmod
        max_transfer_chunk_size: "", // Tamaño máximo de transferencia
        copy_attrs: "0" // Copiar atributos de los archivos
    }
});
```

### Cambio de estado de tópicos (service.topic.change_status)

Servicio empleado para cambiar el estado de los tópicos en Clarive.

```javascript
reg.launch('service.topic.change_status', {
    name: 'Change topic status', // Nombre de la tarea a ejecutar
    config: {
        topics: '123', // ID del tópico que se quiere cambiar
        old_status: '3', // ID del estado del que se parte en el tópico
        new_status: '4', // ID del nuevo estado que se le quiere asignar al tópico
        username: 'clarive' // Usuario al que se le asigna el cambio de estado
    }
});
```

### Creación de tópicos ('service.topic.create')

Servicio empleado para la creación de tópicos en Clarive.

```javascript
reg.launch('service.topic.create', {
    name: 'Create topic', // Nombre de la tarea a ejecutar
    config: {
        title: 'Topic title', // Título del tópico que se va a crear
        category: '34', // ID de la categoría a la que pertenece el tópico
        status: '3', // ID del estado inicial en el que se crea
        username: 'clarive', // Usuario al que se le asigna la creación del tópico
        variables: {desc: 'hello'} // Las distintas variables o campos que tenga el tópico que se va a crear
    }
});
```

### Actualización de tópicos ('service.topic.update')

Servicio empleado para la actualización del contenido de tópicos en Clarive.

```javascript
reg.launch('service.topic.update', {
    name: 'Update topic', // Nombre de la tarea a ejecutar
    config: {
        mid: '123', // ID del tópico que se quiere cambiar
        username: 'clarive', // Usuario al que se le asigna la creación del tópico
        variables: {desc: 'hello'} // Las distintas variables o campos que tenga el tópico que se va a actualizar
    }
});
```

### Borrado de tópicos ('service.topic.delete')

Servicio empleado para el borrado de tópicos en Clarive.

```javascript
reg.launch('service.topic.delete', {
    name: 'Delete topic', // Nombre de la tarea a ejecutar
    config: {
        topics: '123', // ID del tópico que se quiere cambiar
        username: 'clarive' // Usuario al que se le asigna la creación del tópico
    }
});
```
