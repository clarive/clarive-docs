---
title: stash - Almacenamiento del Stash
index: 5000
icon: page
---

El stash en un diccionario de datos clave-valor usado para almacenar los datos que serán compartidos entre las
operaciones en una regla.  Hay dos formas diferentes de acceder al stash y sus valores dependiendo de donde estes
haciendo uso de el.

## Stash dentro de handlers

Si estás llamando al stash dentro de un servicio (controlador o registro), necesitas acceder a él a través de una de las
variables de entrada al handler de este.

```javascript
    var reg = require('cla/reg');
    reg.register('service.test', {
        name: 'Foo Service',
        handler: function(ctx, config) { // En este caso la variable ctx contiene el stash

            ctx.stash('newkey', '1'); // Almacenará el valor '1' dentro de la clave 'newkey' en el stash

            var newkey = ctx.stash('newkey'); // Cogerá el valor que esté dentro de la clave 'newkey'

            return 99;
        }
    });
```

## Stash fuera de controladores

Si estás llamando al stash fuera de un servicio, puedes usar la funcion cla.stash() para acceder al stash.  De la misma
forma que se accedia anteriormente, pero esta vez no necesita hacer uso de variables o funciones con anterioridad.

```javascript

    cla.stash('newkey', '1'); // Almacenará el valor '1' dentro de la clave 'newkey' en el stash

    var newkey = cla.stash('newkey'); // Cogerá el valor que esté dentro de la clave 'newkey'
```
