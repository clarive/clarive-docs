---
title: stash - Stash storage
index: 5000
icon: page
---

The stash is a data key-value dictionary used to store data that will be shared among operations in a rule.  There are
two different ways to access the stash and its values depending on where you are using it.

## Stash inside handlers

If you are calling the stash inside a service (handlers or registers), you need to call it from one of the handler
function input variables.

```javascript
    var reg = require('cla/reg');
    reg.register('service.test', {
        name: 'Foo Service',
        handler: function(ctx, config) { // In this case, the variable ctx contains the stash

            ctx.stash('newkey', '1'); // Will store the value '1' within the key 'newkey' in the stash

            var newkey = ctx.stash('newkey'); // Will take the value from the key 'newkey'

            return 99;
        }
    });
```

## Stash outside handlers

If you are calling the stash outside the service, you can access it using the function cla.stash() Access is the same as
before, except this time there is no need to use functions or variables beforehand.

```javascript

    cla.stash('newkey', '1'); // Will store the value '1' within the key 'newkey' within the stash

    var newkey = cla.stash('newkey'); // Will take the value from the key 'newkey'
```
