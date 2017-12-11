---
title: Writing import modules
index: 3900
---

You can write your own ops into rulebooks. They are called
_import modules_, but think of them as libraries.

These libraries should be checked into your git repository,
right next to your `.clarive.yml`. We recommend using the `.clarive`
directory for them, but you can use any directory really.

Here's a proposed repository structure:

     .clarive.yml
     .clarive/
     .clarive/myop.py         # these must be executable files
     .clarive/anotherop.rb
     src/                     # the rest of your app, not related to Clarive
     ...

Once you push the above structure, your `.clarive.yml` rulebook
will be able to use the `.clarive/` ops as such:

```yaml
import:
   - myproject/myrepo/.clarive/
build:
    - myop:
         some_arg: "do this"
    - anotherop:
         some_arg: "do that"
```

### Making ops runnable

For import module ops to work, they must be commited into your repository as
executables `+x`.

You also need to tell Clarive how to run them. Use the shebang header
to define the executable:

```python
#!/usr/bin/env python

print( "hello from python" );
```

Each op will run in a docker container environment.
To control which container runs each op, set the `image:` param in the import
list:

```yaml
import:

   - path: myproject/myrepo/.clarive/myop.py
     image: python

   - path: myproject/myrepo/.clarive/anotherop.rb
     image: ruby
```

If you don't set an image, they will run in the Clarive
default rulebook container, `clarive/rulebook-runner`.

### Op Naming

The imported ops will have the same name as the
file they are imported from, minus the extension.
If the file is called `myfile.py`, the op will be called
`myfile:` in rulebook.

Duplicate filenames but with with different extension will
give out an error: `duplicate moniker`.

You can also import your ops into a namespace, so that they
are prefixed.

```yaml
import:

   - path: myproject/myrepo/.clarive/
     into: foo

do:
   - foo/myop:
       some_arg: "here"
```

### Reading input args

You ops may need input data to work.
Clarive always sends input data. It's up to
your op module to read it.

Input args are sent through __standard input__ as a __hash__ object in
__JSON__ format.

Therefore, to read it, you need to:

1. read a string from standard input.

2. parse it as JSON with a JSON parser.

```python
#!/usr/bin/env python

import os
import json

input = json.loads( raw_input() )
```

And now you have a dictionary in your python module, ready to be used.

### Returning output args

If you need your op to return structured data back into
your rulebook, you have to __convert data to JSON__ and __print it to standard output__.

The JSON data printed output must be prefixed by the `CLARIVE_RETURN` environment variable
value.

1. Get the environment value for `CLARIVE_RETURN`

2. Encode the JSON with `CLARIVE_RETURN` and your data structure.

3. Print the results to standard output.

```python
print( json.dumps({ os.environ["CLARIVE_RETURN"]: { myarg: "return data" }) )
```

### Examples

Here are a few complete examples of import modules:

1. [Python](/rulebook/python)
2. [NodeJS](/rulebook/nodejs)
3. [Ruby](/rulebook/ruby)

### Testing in the REPL

You can use the [REPL](/concepts/repl) to test your import
modules.

When testing in the REPL, you need to checkout the repository first
with the `workspace:` op. If you don't check it out from the
repository, the `import:` op will attempt to do that for you.

```yaml
workspace:
   - myproject/myrepo
import:
   - myproject/myrepo/.clarive/
```

Is equivalent to this:

```yaml
import:
   - myproject/myrepo/.clarive/
```

But you lose control over the checked out branch:

```yaml
workspace:
   - myproject/myrepo:mybranch
import:
   - myproject/myrepo/.clarive/
```
