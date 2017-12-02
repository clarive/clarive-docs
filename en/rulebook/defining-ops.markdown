---
title: Defining Custom Ops
index: 500
---

You can define and organize your code into custom ops.
Custom ops can then be combined and reused in your
code to avoid repeating tasks continuously.

For example:

```yaml
def:
  tarball:
     - cd /clarive/myproject/myrepo
     - chmod -r +x *
     - rm -rf .git
     - tar cvzf ../myrepo.tgz *
build:
  - tarball:
  - ship:
      host: remoteserver
      from: /clarive/myproject/myrepo.tgz
      to: /remotedir/
```

## Declaring arguments

Op definitions can have signatures declaring required arguments.

```yaml
def:
   my_op (name):
      - echo: hello ${name}
do:
   - my_op:
       name: hannah
```

The parenthesis above declares `name` as a required argument.
The same op above could have been declared more verbosely as such:

```yaml
def:
   my_op:
     required:
        - name
     do:
      - echo: hello ${name}
do:
   - my_op:
       name: hannah
```

Failing to call the op with the argument `name` will result
in an error:

```yaml
def:
   my_op (name):
      - echo: hello ${name}
do:
   #  this will error: Missing required arg `name` for `def: my_op (name)`
   - my_op:
        another_param: whatever
```

If the op has no required arguments, remember to use
a colon to indicate to the parser that you intend to call
an op instead of running a simple shell command:

```yaml
def:
   ls_tmp:
      - ls -lart /tmp
do:
   - ls_tmp:
   - echo: "the above is perfectly fine"
```

If you want to just send a single string value argument to the defined op, you
have to set _exactly one argument_ to the op you are defining, as such:

```yaml
def:
   ls_tmp (dir):
      - ls -lart ${dir}
do:
   - ls_tmp: /tmp
```

You can do the same with arrays:

```yaml
def:
   npm_install (packages):
      - foreach:
          var: pkg
          in: ${packages}
          do:
             - npm install ${pkg}
do:
   - npm_install:
      - lodash
      - react
```

## Returning values

You can also return values from your defined ops
using the `return` op.

```yaml
def:
   my_op (name):
      - return:
            message: hello ${name}
do:
   - ret = my_op:
       name: hannah
   - echo: my op said ${ret.message}
```

Return values do not to be previously declared.  But if they are, the rulebook
runner expects the promised return values to be returned, otherwise an error
will be thrown.

Even though they are not mandatory, we recommend using return value
declarations to make your code more readable.

## Constant Variables

Defs cannot read from global variables. The idea
is that your `def` ops be __isolated__ from the surronding
environment, following a more functional programming style:

```yaml
vars:
   global_path: 'my/path/'
def:
   ## error: this will not work, ${global_path} is not available to your
   ##        defined op:

   write:
         - write_file:
             body: "hello world"
             file: ${global_path}/myfile.txt
```

Instead, create a variable `var`section within your `def` op:

```yaml
def:
   write:
         - var:
             path: 'my/path'
         - write_file:
             body: "hello world"
             file: ${path}
```

Or send the variable as an argument to your op:

```yaml
vars:
   global_path: 'my/path/'
def:
   write (path):
         - write_file:
             body: "hello world"
             file: ${path}
do:
   - write:
        path: ${global_path}
```
