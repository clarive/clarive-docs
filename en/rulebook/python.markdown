---
title: Writing import modules with Python
index: 4000
---

Here's an example of a Python import module that could serve as an skeleton.

It should be compatible with both Python 2 and 3.

```python
#!/usr/bin/env python

import os
import json

input = json.loads( raw_input() )

print( "Hello {0} from my module".format( input["quux"] ) )

output = { "foo": { "bar": input["quux"] } }

print( json.dumps({ os.environ["CLARIVE_RETURN"]: output }) )
```

!!! warning
    Don't forget to apply the execute flag `+x` to your import modules.
    Clarive rules can only invoke modules that are executable.
    Make sure that the shebang `#!` definition points to a valid
    binary in the docker container image that will be used with
    your module.

To test the above Python import module from the command line, try the
following command:

```bash
echo '{ "quux": 123 }' | CLARIVE_RETURN=1234 ./hello.py
```

If everything went well, the following output should be shown.

```yaml
Hello from my module
{"1234": {"myvar": {"bar": 123 }}}
```

## Using Python imports in your rulebook

To use a Python module you have to first check it into a Git repository managed
by Clarive.

Let's suppose there is a project called `MyProject` set up in your system, and
that the project has a Git repository called `MyRepo`. Therefore the path to your
rulebook and module would be:

```bash
/MyProject/MyRepo/.clarive.yml
/MyProject/MyRepo/.clarive/python/hello.py
```

Now in your rulebook import the Python file with the `import:` directive.
You can try this using the the [REPL](/concepts/repl).

```yaml
image: python
workspace:
   - MyProject/MyRepo
import:
   - /MyProject/MyRepo/.clarive/python
do:
   - echo: "and now for something completely different:"
   - hello:
        quux: "world"
```
