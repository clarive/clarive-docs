---
title: Extending the JS system with modules
index: 2000
icon: page
---

To extend the JS code we recommend using 2 strategies:

## Modules

Clarive follows CommonJS specification for loading modules, you can divide your javascript building blocks accross
multiple files, `export` needed functions and then `require` them where needed.

For example:

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

User included modules is recommended to be stored in the filesystem, under `CLARIVE_BASE/plugins/[plugin-name]/modules`
folder.

To create the modules folder, we recommend creating a plugin first in your `CLARIVE_BASE` [location](/setup/directories)

```javascript
// create the file plugins/myplugin/modules/myutil.js:
exports.doThis = function(num) {
    print("This is it: " + num);
};

// now use it in your code
var myutils = require("myutil");
myutils.doThis(123);
```

## Rules

Write an independent rule with common logic needed by other rules. Then invoke that rule as part of your code.

Write a rule with a JS CODE operation with the following content:

```javascript
var something = cla.stash("something");
cla.stash("myresults", something * 1000 );

var stash = { something: 123 };
cla.rule.run('my_rule_runner', stash);
print( "results=" + stash.myresults );  // you get 123000
```

Read more about `cla.rule` [here](/devel/js-api/rule)
