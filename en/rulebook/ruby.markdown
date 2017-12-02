---
title: Writing import modules with Ruby
index: 4100
---

Here's an example of a Ruby import module. Let's call
this file `ruby_hello.rb`:

```ruby
#!/usr/bin/env ruby

require 'json'

input = JSON.parse( gets )
msg = 'hello ' + input['quux'] + ' from ruby'
puts msg

puts JSON.generate( { ENV['CLARIVE_RETURN'] => { "myvar" => { "msg" => msg } } } )
```

!!! warning
    Don't forget to apply the execute flag `+x` to your import modules.
    Clarive rules can only invoke modules that are executable.
    Make sure that the shebang `#!` definition points to a valid
    binary in the docker container image that will be used with
    your module.

To test your Ruby import module from the command line, try the
following command:

```bash
echo '{ "quux": "worlds" }' | CLARIVE_RETURN=1234 ./ruby_hello.rb
```

If everything went well, the following output should be shown.

```yaml
hello worlds from ruby
{"1234":{"myvar":{"msg":"hello worlds from ruby"}}}
```

## Using Ruby imports in your rulebook

To use a Ruby module you have to first check it into a Git repository managed
by Clarive.

Let's suppose there is a project called `MyProject` set up in your system, and
that the project has a Git repository called `MyRepo`. Therefore the path to your
rulebook and module would be:

```bash
/MyProject/MyRepo/.clarive.yml
/MyProject/MyRepo/.clarive/imports/ruby_hello.rb
```

Now in your rulebook import the Ruby file with the `import:` directive.
You can try this using the the [REPL](/concepts/repl).

```yaml
image: ruby
workspace:
   - MyProject/MyRepo
import:
   - /MyProject/MyRepo/.clarive/imports/
do:
   - echo: "and now for something completely different:"
   - ruby_hello:
        quux: "world"
```
