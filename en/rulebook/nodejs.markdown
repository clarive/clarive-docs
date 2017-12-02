---
title: Writing import modules with NodeJS
index: 4200
---

Here's an example of a NodeJS import module that could serve as an skeleton.

```javascript
#!/usr/bin/env node

process.stdin.resume();
process.stdin.setEncoding('utf8');

process.stdin.once('data', function (input) {
    process.stdin.pause();

    input = JSON.parse( input );

    console.log({ [process.env.CLARIVE_RETURN]: { 'hello': input.quux } });
});
```

!!! warning
    Don't forget to apply the execute flag `+x` to your import modules.
    Clarive rules can only invoke modules that are executable.
    Make sure that the shebang `#!` definition points to a valid
    binary in the docker container image that will be used with
    your module.

To test the above NodeJS import module from the command line, try the
following command:

```bash
echo '{ "quux": 123 }' | CLARIVE_RETURN=1234 ./node_hello.js
```

If everything went well, the following output should be shown.

```yaml
{"1234": { "hello": 123 } }
```

## Using NodeJS imports in your rulebook

To use a NodeJS module you have to first check it into a Git repository managed
by Clarive.

Let's suppose there is a project called `MyProject` set up in your system, and
that the project has a Git repository called `MyRepo`. Therefore the path to your
rulebook and module would be:

```bash
/MyProject/MyRepo/.clarive.yml
/MyProject/MyRepo/.clarive/imports/node_hello.js
```

Now in your rulebook import the NodeJS file with the `import:` directive.
You can try this using the the [REPL](/concepts/repl).

```yaml
image: node
workspace:
   - MyProject/MyRepo
import:
   - /MyProject/MyRepo/.clarive/imports
do:
   - echo: "and now for something completely different:"
   - node_hello:
        quux: "world"
```
