---
title: Creating Controllers in JS
index: 5000
icon: page
---

`Controllers` are web endpoints handlers that processes a web request and produces
a web response.

Controllers are used to expose functionality from a Clarive plugin through a URL, they
are needed, for example, to build a dashboard.

The controller is the part that sends response data from the server back to the
interface.

Controllers can only be created in a plugin, and should be part of the load init phase
of a plugin.

## Creating a Controller

To create a controller, just create a JS source file in the `init/` directory of your
plugin (`CLARIVE_BASE/plugins/[plugin-name]/init/`) and inside register a new controller:

```javascript
var reg = require('cla/reg');

reg.controller('foobar',{
    authenticate: false,
    handler: function(req,res){
        res.body( "hello world" );
    }
});
```

`handler` function will run in a new javascript environment on each call, so anything
defined outside `handler` scope will be lost on the next call.

For example:

```javascript
var reg = require('cla/reg');
var test = 'hello world';
reg.controller('foobar', {
    handler: function(req, res) {
        res.body(test); //error: identifier 'test' undefined
    }
});
```

To overcome this limitation we recommend you to put your plugin logic in a separate
module and then require from the `handler` function.

For example:

```javascript
/* modules/handler.js */
var test = 'hello world';
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

This technique will also give you a better error reports with file name and line number.

### Controller URL

Controller URL can be accessed at:
`http://clariveserver/plugin/[plugin-name]/[controller-name]`.

For instance, let's suppose you created
`CLARIVE_BASE/plugins/myplugin/init/controllers.js` plugin and registered the following
controller:

```javascript
var reg = require('cla/reg');

reg.controller('foobar',{
    authenticate: false,
    handler: function(req,res){
        res.body( "Hello " + req.username() );
        res.contentType('text/html');
    }
});
```

Then you can access this controller at:
`http://clariveserver/plugin/myplugin/foobar`

Controller handler pass 2 arguments, request and response objects.

## Request Object

Provides information about the current client request. The request object contains web
endpoint input, and is typically sent by the browser.

The request object is the first argument to a Controller handler, which in this document
will be identified as `req`.

#### req.args()

Contains an Array of path parts, omitting the first path ("plugin").

    /plugin/myplugin/mycontroller/path/part/one

Will result in the following Array:

    [ 'myplugin', 'mycontroller', 'path', 'part', 'one' ]

#### req.address()

IP address of the client.

#### req.contentType()

Shortcut for the `Content-Type` client header.

#### req.contentLength()

Shortcut for the `Content-Length` client header.

#### req.contentEncoding()

Shortcut for the `Content-Encoding` client header.

#### req.cookie(id)

This method returns a cookie value as an Object that has special convenience methods
which make it easy to extract the contents of a cookie such as value and date.

```javascript
reg = require('cla/reg');

reg.controller('mycontroller', {
    handler: function(req,res) {
        var mycookie = req.cookie('mycookie')
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

#### req.cookies()

This method returns all cookies as an Object, with key-value pairs. In contrast to
`req.cookie()`, the values are stringified instead of objects.

#### req.env()

Returns the current environment for the call.

#### req.header(headerkey)

Returns value of a given `header key`.

#### req.method()

Returns the request method, ie `GET`, `POST`, `DELETE` etc.

The request method is useful for dispatching different behaviors based on the method
requested, like when implementing REST interfaces.

#### req.param(key)

Returns the request query or body (form) parameter for the given key.
This includes both `GET` and `POST` parameters.

Example, for the following URL request:

    http://clariveserver/plugin/myplugin/mycontroller?foo=bar

Use:

    print( req.param("foo") );

To get foo's value `bar`.

#### req.protocol()

Returns the protocol used for the request, such
as `http` or `https`.

#### req.query(key)

Returns the value for the parameter key given in a request query (from a `GET`).

This is similar to the `req.param()` function but only returns query parameters, ignoring
body parameters (forms).

#### req.read([maxlength])

Reads a chunk of data from the input.

Use `maxlength` to limit the number of bytes read.
It defaults to the size of the request if not specified.

Returns `undefined` when the stream has ended, so it's suitable to be used in a `while()`
loop.

```javascript
var str = '';
var ch;
while( ch = req.read(1) ) {
    str += ch;
}
```

#### req.remoteUser()

Returns the remote user from the header.

#### req.secure()

Returns true or false, indicating whether the connection is secure (https).

#### req.uri()

Returns the request URI object.

#### req.userAgent()

Returns user agent request header, which typically contains the browser version.

#### req.user()

Returns a Clarive user object, which includes the following attributes:

```javascript
    var user = req.user();
    user.ci(); // the CI object
    user.isRoot(); // true if a user has administrator permissions
    user.username(); // the username id string of the user logged into Clarive
    user.languages(); // returns an Array with the languages the user prefers
    user.hasAction('action.foo.bar'); // checks if user has a given action
```

#### req.username()

Returns the user id of the user logged in Clarive.

## Response Object

### Serving JSON

To send a JSON response, use `res.json()` method. Clarive will take care of serializing
and encoding the data correctly.

```javascript
    handler: function(req,res){
        res.json({ aa: 100, bb: 200 });
    }
```

### Serving Files

### Unicode Response
