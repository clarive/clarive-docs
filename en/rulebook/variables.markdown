---
title: Variables and Templating
index: 200
---

Rulebooks can make use of a variable replacement and
templating system based on ClaJS, a very fast Javascript
interpreter that comes bundled with Clarive.

- `${myvar}` - simple variable parsing
- `{{ myvar }}` - Javascript variable parsing


Your rules can use either one in the code.

## Defining variables in a rule

To define variables in a rule, write them in the `vars` section
at the beginning of the rulebook.

```yaml
vars:
   - logfile: /tmp/mylogfile.log
do:
   - $ echo "what an error" > {{logfile}}
```

```yaml
vars:
   - logdir: /tmp
   - logfile: "{{logdir}}/mylogfile.log"
do:
   - $ echo "what an error" > {{logfile}}
```

`vars` is an array of variable definitions.

## Setting variables with `var`

Optionally, vars can be defined as you go in your rule code.

```yaml
do:
   - var:
       foo: world
   - echo: hello {{ foo }}
```

To assign values that go beyond a single line, use YAML multiline
strings with the pipe operator.

```yaml
vars:
   - mytext: |
        this is
        a very long value
do:
   - write_file:
        body: "{{ mytext }}"
        file: /tmp/myfile.txt
```

## Inline setting with `=`

There's a very convenient short notation for setting variables
using the equal `=` operator.

```yaml
do:
   - cmd =: npm
   - package =: yaml
   - ${cmd} install ${package}
```

The equal operator can be used with anything that
returns a value, such as an op defined with `def`
or a shell command.

```yaml
def:
   package_list:
      - return:
           - haml
           - sass
do:
   - packages = package_list:
   - foreach:
        var: pkg
        in: ${packages}
        do:
           - gem install ${pkg} --install-dir /tmp/gems
```

Shell commands results can be assigned to variables too, but there has to be an
added `$` dollar sign prefixed to the command. This is so that the rulebook
parser can correctly differentiate between rule variables and shell variables.
If the command fails when being assigned to a variable, the error is not thrown
and instead returned into the variable.

```yaml
do:
   - results = shell: ls /tmp/
   - foreach:
        var: line
        in: "{{ results.output.split('\\n') }}"
        do:
           - echo: LINE=${line}
```

## Setting variables with the `set` op

You can use the `set` op to set variables.
The difference with other variable setting methods is that `set`
allows you to _make the variable name itself variable_.

```yaml
do:
   - set:
        var: package
        value: react
   - echo: "Ready to install ${package}..."
   - npm install ${package}
```

## Importing variables from a file

You don't have to keep all your vars in a `.clarive.yml` file.
They can be stored separately in variable files and be loaded
into the rule using the `parse` op.

```yaml
# .clarive/myvars.yml
foo: bar
logdir: /var/logs
logfile: "{{ logdir }}/mylog.log"
```

Then load the file with `parse` and assign it to the variable
`myvars`:

```yaml
do:
   - myvars = parse:
       file: .clarive/myvars.yml
   - echo: imported {{ myvars.foo }}
```

Be aware that YAML interprets the following:

```yaml
var:
   foo: {{ myvar }}
```

As the assignment of a ill-defined hash `{ ... }` to the variable `foo`.
You have to put quotes around the handlebars, or use a multi-line `|` string so that the
YAML parser treats as a valid.
