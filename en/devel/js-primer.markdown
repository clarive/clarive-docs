---
title: A JavaScript Primer
index: 2000
icon: page
---

This is a quick primer to help you getting started with Javascript in case you
never seen it before.

To try this out, use the Clarive REPL.
The REPL is a useful tool to getting started with JavaScript
within the Clarive automation environment. Refer to the [REPL](/devel/repl) documentation
to learn more.

## Hello World

This is the most basic program you can
write:

```javascript
print('Hello world');
```

## Basic Syntax

All Clarive JS programs are strict by default. That's done
by setting a `"use strict;" at the beginning of code evaluation.

So this code will fail:

```javascript
xx = 20;
print(xx); // syntax error due to undefined variable xx
```

## Declaring variables

Variables are declared with the keyword `var`.
JavaScript has no types, so you don't need to
define its type.

```javascript
var foo;
foo = 100;
var bar = 10;
var age,time,address;
```

## Conditionals

Conditionals in JavaScript is done with the `if`
instruction:

```javascript
var foo = false;
if( foo ) {
    bar();
} else {
    // ...
}

// you can also use switch-case to dispatch conditional values

var xx = 100;
switch(xx) {
    case 100:
    print('low');
    break;
    case 200: print('high');
}
```

## Loops

Loops allows us to repeat a block of code many times over.
Most loops in JS are built using `for` and `while`.

```javascript
for( var i=10; i<100; i++ ) {
    print("Hello " + i);
    if( i > 20 ) {
        break;
    }
}
```

Another elegant and clever way to iterate through arrays is to use `map()`
which is natively supported in the Clarive JS.

```javascript
var arr = [1,2,3];
arr.map(function(el){
    print( "This is " + el );
});
```

## Arrays

```javascript
var arr = [];
arr.push( 100 );

var arr2 = [1,2,3];
var arr3 = arr2.concat( arr, 100 );

print( arr3.join(',') );
```

## Objects

```javascript
var obj = {};
obj[ 'myvalue' ] = 100;

// object keys can also be nested
obj = { address: {} };
obj['address']['zip'] = 90210;
```

You can also use shorthand notation:

```javascript
var obj = { myvalue: 200 };
// these are the same:
print( obj.myvalue );
print( obj[ 'myvalue' ] );
```

## Functions

```javascript
function nada(name) {
    return "Nada is everything, dear " + name;
}

print( nada("Bob") );
```

## The console

A set of JavaScript `console` methods are implemented
in Clarive JS.

```javascript
console.log({aa:11});
console.warn('hello there');  // to standard error
console.dir({aa:22});
console.info({aa:22});
console.assert(true, 'nada');
```

## Templating and multiline strings

For writing multi-line strings that can also be templated (ie. that have variables interpolated),
Clarive implments the Ecmascript ES6 templating literals
standard.

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals <img class='ext-link' src='/static/images/icons/window-new.svg' />](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)

This is done by enclosing your string between backticks:

```javascript
var txt = `This is
a muiltiline
string
`;

print(txt);
```

This is also a good templating mechanism since it
can be interpolated with expressions (including variables)
that can be executed as javascript in a function.

```javascript
var name = 'Joe';
var address = `111 Elm St.
Nowhere, NY 10001
`;
var html = `
<div>
    <strong>${name}</strong>
    <strong>${address}</strong>
</div>
`;

print(html);
```

Not only variables can be interpolated, but also expressions:

```javascript
num = 100;
print(`
This is normal: ${num}
This is double: ${num * 2}
`);
```

To escape interpolation of variable and expressions,
use backslash: `\${...}`

```javascript
var bashScript = `
echo \${var};
exit 1;
`;
```

### Heredocs

Templated strings can be extremely powerful, so *heredocs*
(or [here-documents <img class='ext-link' src='/static/images/icons/window-new.svg' />](https://en.wikipedia.org/wiki/Here_document)),
a simpler, multi-line string format is also implemented.

The advantage of using heredocs is that it avoids having to
escape templated variables (ie. `${myvar}`) which can clash
with the current Clarive variable system, which also uses
the Ecmascript `${...}` enclosure for variable formatting.
Also, other scripting languages and templating systems share
this enclosure (ie. Bash, Perl, etc.) so it's always handy to be able to
count on a *non-interpolated*  multi-line string such as heredocs.

A here-document allows you to create a string that spreads on multiple lines
and preserves white spaces and new-lines. If you run the following code it will
print exactly what you see starting from the word Dear till the line before the
second appearance of END_MESSAGE.

The here document starts with two less-than characters `<<` followed by an
arbitrary string that becomes the designated end-mark of the here-document,
followed by the semi-colon `;` (or newline) marking the end of the statement.

This is a bit strange as the statement does not really end here. Actually the content of the
here document just starts on the line after the semi-colon, (in our case with
the word "Dear"), and continues till perl finds the arbitrarily selected
end-mark. In our case the string END_MESSAGE.

All of these are valid uses of heredocs.

```javascript
var str = <<END_MESSAGE;
So here it starts.

A long "string".

END_MESSAGE

// note that the closing END_MESSAGE above does not have an ending semicolon ;
print(str);
```
Another example, no semicolon after the end-mark.

```javascript
var str = <<"END"
Hello.

There.

END
print(str);
```

Chosing the right end-mark is the trick for holding long, abritary
strings. End marks cannot have spaces and only alphanumeric character,
plus underscore `_`.

## Error management

Error raising should be done using the
`throw` statement (unless a Clarive JS logging error is to be thrown, in which
case it's better to use the more powerful `cla.error()` function).

To catch errors, use the `try-catch` statements.

```js
try {
    if( somethingIsNotright ) {
        throw new Error("This is not ok");
    }
    // ... keep processing here ...
} catch(e) {
    print( "Error caught on tape, everything under control: " + e);
}
```

## General JavaScript Error Messages

Here are some of the general, language related
error messages that can be issued by the Clarive JS
interpreter.

### `TypeError: invalid base value`

This error indicates that either a method or attribute
is being called on an undefined variable, where typically
an Object or Array type was expected.

For example:

```js
var myfunc = function(){ return undefined };
var foo = myfunc();  // say myfunc() returns undefined
print( foo.arg );   // Invalid base value error
print( foo.doIt() );   // Invalid base value error too
```

To fix it, always check for undefined or null objects and arrays before
calling methods or attributes on objects you are not sure are correct.

```js
var myfunc = function(){ return undefined };
var foo = myfunc();
if( foo != undefined ) {
    print( foo.arg );
} else {
    throw new Error("Not the value I expected!");
}
```

### `ReferenceError: identifier '...' undefined `

This error is thrown when there's an attempt to
use a variable or function that has not been defined.

```
print( xxx );
// ReferenceError: identifier 'xxx' undefined
```

Remember that Clarive JS has strictures turned on by default,
which requires every variable to be declared in the current context.

### `TypeError: not callable`

This error occurs when trying to call a method that
is not part of an object. For example:

```js
var obj = { age: function(){ return 19 } };
print( obj.age() ); // prints 19
print( obj.name() ); // TypeError: not callable
```

### `SyntaxError: parse error`

This error may be caused by an internal error, which
can be probably have more data or info further down the message.

### `SyntaxError: error parsing token`

Error caused by an invalid JavaScript syntax, such as
using invalid or incorrect characters.

### `SyntaxError: unterminated statement`

This error usually indicates there is a missing semicolon `;`
somewhere in the code.

## Modules Included

Clarive JS can load JavaScript modules from the filesystem.
The software is shipped with useful modules such as Handlebars.js
and Underscore.js.

More can be included by adding them to
the `plugins/[plugin]/modules` directory in the Clarive base.

[Read more about plugins here](/devel/plugins/intro).

### Handlebars

Handlebars are a templating system, for replacing
strings within another from data.

```javascript
var hs = require('handlebars');
var tt = "Hi there,\
    this is {{mom}}\
    ok?\
    ";
var foo = hs.compile(tt);
print( foo({ mom: "Johanna"}) );
```

For more info, read the [Handlebars.js library reference <img class='ext-link' src='/static/images/icons/window-new.svg' />](http://handlebarsjs.com/)

### Underscore

Underscore.js is a utility library
that adds plenty of handy functions to
the global object `\_` (underscore).

```javascript
var _ = require('underscore');
_.each([1,2], function(x){ print(x) });
```

For more info, read the [Underscore library reference <img class='ext-link' src='/static/images/icons/window-new.svg' />](http://underscorejs.org/)

## Not implemented in Clarive

The following is not implemented by the
Clarive JS server interpreter:

- `alert()`, `confirm()` and other messaging features
- `console.log()` and other `console` methods
- `window`, `document` and other DOM-related features
- `system.` and other NodeJS features
- an evented machine: Clarive JS has a blocking interface and code is non-reentrant

So, basically, just remember:

- ***Clarive JS is not a browser interpreter, it has no DOM or similar concept***
- ***Clarive JS is not NodeJS***

## Recommended Reading

Our intention here is just to give the reader
enough basic concepts for getting off the ground
with the language.

For more in depth learning of the JavaScript language, actually called **Ecmascript**,
we recommend the following reference:

- The Mozilla JavaScript guide: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide <img class='ext-link' src='/static/images/icons/window-new.svg' />](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
- JavaScript "The Good Parts" book [http://bdcampbell.net/javascript/book/javascript_the_good_parts.pdf <img class='ext-link' src='/static/images/icons/window-new.svg' />](http://bdcampbell.net/javascript/book/javascript_the_good_parts.pdf)
