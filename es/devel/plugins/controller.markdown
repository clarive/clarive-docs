---
title: Crear Controladores en JS
index: 5000
icon: page
---

Los `controladores` de endpoints web procesan una solicitud web y producen una respuesta web.

Estos se utilizan para exponer la funcionalidad de un plugin de Clarive a través de la URL, por ejemplo, para crear un
panel de control.

El controlador es el componente que envía los datos de respuesta del servidor a la interfaz.

Los controladores sólo se pueden crear en un plugin y deben formar parte de la fase de carga de un plugin.

## Creación de un controlador

Para crear un controlador, simplemente cree un archivo fuente JS en el directorio `init /` de su plugin
(`CLARIVE_BASE/plugins/[plugin-name]/init/`) y registre un nuevo controlador en él:

```javascript
var reg = require('cla/reg');

reg.controller('foobar',{
    authenticate: false,
    handler: function(req,res){
        res.body( "hola mundo" );
    }
});
```

La función `handler` ejecuta en un nuevo entorno javascript en cada llamada, de modo que cualquier cosa definida fuera
del alcance de la función `handler` se perderá en la próxima llamada.

Por ejemplo:

```javascript
var reg = require('cla/reg');
var test = 'hola mundo';
reg.controller('foobar', {
    handler: function(req, res) {
        res.body(test); //error: identifier 'test' undefined
    }
});
```

Para evitar esta limitación, le recomendamos que coloque su lógica de complemento en un módulo aparte y luego requerirlo
de la función `handler`.

Por ejemplo:

```javascript
/* modules/handler.js */
var test = 'hola mundo';
var another = require('./another.js');
module.exports = function(req, res) {
    res.body(test);
};

/* init/myplugin.js */
var reg = require('cla/reg');
reg.controller('foobar', {
    handler: function() {
        return require('handler').apply(this, arguments);
    }
});
```

Esta técnica también le dará un mejor informe de errores con nombre de archivo y número de línea.

### Controlador URL

Puede acceder a la URL del controlador en: `http://clariveserver/plugin/[plugin-name]/[controller-name]`.

Por ejemplo, supongamos que creó plugin `CLARIVE_BASE/plugins/myplugin/init/controllers.js` y registró el siguiente
controlador:

```javascript
var reg = require('cla/reg');

reg.controller('foobar',{
    authenticate: false,
    handler: function(req,res){
        res.body( "hola " + req.username() );
        res.contentType('text/html');
    }
});
```

A continuación, puede acceder a este controlador en: `http://clariveserver/plugin/myplugin/foobar`

El handler del controlador pasar 2 argumentos, solicitudes y objetos de respuesta.

## Objeto Request

Proporciona información acerca de la solicitud actual del cliente. El objeto request contiene Entrada de punto final
web, y normalmente se envía por el navegador.

El objeto request es el primer argumento para un handler controlador, que en este documento será identificado como
`req`.

#### req.args()

Contiene una matriz de partes de ruta, omitiendo la primera ruta ("plugin").

    /plugin/myplugin/mycontroller/path/part/one

Dará como resultado el siguiente Array:

    [ 'myplugin', 'mycontroller', 'path', 'part', 'one' ]

#### req.address()

Dirección IP del cliente.

#### req.contentType()

Atajo para el encabezado de cliente `Content-Type`.

#### req.contentLength()

Atajo para el encabezado de cliente `Content-Length`.

#### req.contentEncoding()

Atajo para el encabezado de cliente `Content-Encoding`.

#### req.cookie()

Este método devuelve todas las cookies como un objeto, con pares clave-valor.  En contraste con `req.cookie ()`, los
valores son stringificados en lugar de objetos.

```javascript
reg = require('cla/reg');

reg.controller('mycontroller',{
    handler: function(req,res){
        var mycookie = req.cookie()
        res.body(
            'name=' + cookie.name() +
            'value=' + cookie.value() +
            'path=' + cookie.path() +
            'expires=' + cookie.expires() +
            'maxAge=' + cookie.maxAge()
        );
    }
});
```

#### req.env()

Devuelve el entorno actual de la llamada.

#### req.header(headerkey)

Devuelve el valor de una `clave de encabezado` dada.

#### req.method()

Devuelve el método de solicitud, ie `GET`, `POST`, `DELETE` etc.

El método de solicitud es útil para distribuir diferentes comportamientos basados en el método solicitado, como al
implementar interfaces REST.

#### req.param(key)

Devuelve la consulta de solicitud o el parámetro body (form) para la clave dada.  Esto incluye los parámetros `GET` y`
POST`.

Ejemplo, para la siguiente solicitud de URL:

     http://servidor-clarive/plugin/miplugin/micontrolador?foo=bar

Utilizar:

    print( req.param("foo") );

Para obtener el valor de foo `bar`.

#### req.protocol()

Devuelve el protocolo usado por la solicitud, tales como `http` o `https`.

#### req.query(key)

Devuelve el valor para el parámetro clave dado en una solicitud (de un `GET`).

Esto es similar a la función `req.param ()` pero sólo devuelve los parámetros de la consulta, ignorando los parámetros
del cuerpo

#### req.read([maxlength])

Utilice `maxlength` para limitar el número de bytes leídos.  El valor predeterminado es el tamaño de la solicitud si no
se especifica.

Devuelve `undefined` cuando el flujo ha terminado, por lo que es adecuado para ser utilizado en un bucle `while ()`.

```javascript
var str = '';
var ch;
while( ch = req.read(1) ) {
    str += ch;
}
```

#### req.remoteUser()

Devuelve al usuario remoto del encabezado.

#### req.secure()

Devuelve true o false, indicando si la conexión es segura (https).

#### req.remoteUser()

Devuelve el usuario remoto del encabezado.

#### req.secure()

Devuelve *true* o *false*, indicando si la conexión es segura (https).

#### req.uri()

Devuelve el objeto URI de la petición.

#### req.userAgent()

Devuelve el encabezado de solicitud del agente de usuario, que contiene la versión del navegador.

#### req.user()

Devuelve un objeto de usuario Clarive, que incluye los siguientes atributos:

```javascript
    var user = req.user();
    user.ci(); // the CI object
    user.isRoot(); // true if a user has administrator permissions
    user.username(); // the username id string of the user logged into Clarive
    user.languages(); // returns an Array with the languages the user prefers
    user.hasAction('action.foo.bar'); // checks if user has a given action
```

#### req.username()

Devuelve el ID de usuario del usuario logueado en Clarive.

## El Objeto de Respuesta

### Sirviendo a JSON

Para enviar una respuesta JSON, use el método `res.json ()`. Clarive se encargará de serializar y codificar los datos
correctamente.

```javascript
    handler: function(req,res){
        res.json({ aa: 100, bb: 200 });
    }
```

### Servir Archivos

### Respuesta Unicode
