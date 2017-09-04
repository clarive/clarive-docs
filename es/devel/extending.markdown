---
title: Extendiendo el sistema JS a través de módulos
index: 2000
icon: page
---

Para extender el código JS recomendamos utilizar dos estrategias:

## Módulos

Clarive sigue la especificación CommonJS para cargar módulos, puede dividir sus bloques de construcción javascript entre
varios archivos, `exportar` funciones necesarias y luego `requerirlas` donde sea necesario.

Por ejemplo:

```javascript
/* foo.js */
var Foo = function () {};
Foo.prototype.log = function () {
  console.log('Foo!');
};

exports.Foo = new Foo();

/* foo/bar.js */
module.exports = function(){
    console.log('fooBar!');
};

/* index.js */
var foo = require('./foo');
var bar = require('./foo/bar.js');

foo.log(); // Foo!
bar();     // fooBar!
```

Se recomienda que los módulos incluidos por el usuario se almacenen en el sistema de archivos, bajo la carpeta
`DECLARATIVE_BASE/plugins/[nombre-plugin]/modules`.

Para crear la carpeta de módulos, se recomienda crear antes el plugin en el [directorio](/setup/directories)
`CLARIVE_BASE`.

```javascript
// crear el fichero plugins/myplugin/modules/myutil.js:
exports.doThis = function(num) {
    print("Esto es: " + num);
};

// Ahora uselo en su código
var myutils = require("myutil");
myutils.doThis(123);
```

## Reglas

Escribe una regla independiente con la lógica necesaria para ser usada por otras reglas. Luego invocar esa regla como
parte de su código.

Escriba una regla con una operación en código JS con el siguiente contenido:


```javascript
var something = cla.stash("something");
cla.stash("myresults", something * 1000 );

var stash = { something: 123 };
cla.rule.run('my_rule_runner', stash);
print( "results=" + stash.myresults );  // obtienes 123000
```

Lea más sobre `cla.rule` [aquí](/devel/js-api/rule)
