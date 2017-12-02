---
title: Writing Sane YAML
index: 999
---

YAML is a markup language that has some neat features
but also many traps and pitfalls.

## Using comment lines

You can use comment lines in YAML. Just start a line
with the hash/pound character, just like in many shell-scripting
languages:

```yaml
# comment here
do:
         ### indenting is not important for comments
   # now for some action
   - npm install yaml  # some self referencing here...
   # this is important too:
   - npm install someotherthing
```

Comments are stripped out during parsing and do not interfere
with your commands.

## Error handling

When a rulebook is processed, the very first thing
the Clarive rulebook engine does is __parse__ the YAML
structure.

The Clarive rulebook parser tries to catch as many YAML errors
as possible during the YAML parsing phase. YAML parsing
errors look like this:

```yaml
error parsing YAML YAML::XS::Load Error: The problem:

    mapping values are not allowed in this context

was found at document: 1, line: 2, column: 16
1:
2:   - echo: hello:
------------------^
3:
```

The above error is pointing to an invalid YAML structure, one unexpected colon
inside the value for the op `echo`.  The line-and-arrow `------^` underneath
line 2 points to the invalid character detected by the YAML parser.

## Common pitfalls

Most YAML errors can be avoided following a few guidelines
highlighted here.

### Nesting

Make sure to nest your structures correctly.
The rulebook YAML parser requires at least __1 space__ for indenting
elements in YAML.

```yaml
# one space indenting is pushing it a little
do:
 - ls /tmp
 - exit 0
```

Be careful with flat hash ops, such as `try-catch` and `if-then-else`.
The keys need to be perfectly aligned for it to be parsed and compiled
correctly:

```yaml
do:
   - if: '{{ 1 == 1 }}'
     then:
        - npm install yaml
     else:
        - fail: not true there
```

Pay attention to the above `if-then-else` ops.  They are perfectly aligned at
column 6. Any misaligning and they will not be interpreted correctly.

### Use quotes abundantly

YAML slurps in key values without quotes, which can be very convenient.
But get used to quoting your strings. It improves readability and reduces errors.

```yaml
do:

  # this works
  - echo: hello world

  # but this is more readable
  - echo: "hello world"
```

### Values that look like nested YAML

As in the error shown above, using colons inside your string values
can be interpreted as hash keys by the parser:

```yaml
do:
  # nasty errors here
  - echo: hello: world
```

### Handlebar template errors

Handlebar template blocks `{{ ... }}` can be easily confused
with hash structures such as `{ foo: 100, bar: 200 }`.
The YAML parser most likely will not error off on this one and
your handlebar block will be treated as an invalid hash that will
generate errors further down the road, into the compiling or running phases.

The solution is to use quotes around handlebar blocks to prevent confusing the
rulebook engine.

```yaml
do:
  - echo: "{{ 'this is ' + 10 + ' times better' }}"
```

### Escaping special characters

YAML interprets special control characters, such as `\n` or `\t`.
When combined with certain ops or shell commands it may generate unexpected errors
at odd spots that look right, specially with handlebar `{{ ... }}` ClaJS code.

This for instance will not be correctly parsed by the ClaJS engine. The
newline needs to be escaped, otherwise the YAML parser will introduce a newline
__before__ the text is processed by the ClaJS runner.

```yaml
do:
   - mydata =: |
         line1
         line2
   - lines =: "{{ mydata.split('\n') }}"   # this will fail with a JS error
   - lines =: "{{ mydata.split('\\n') }}"  # now that's better
```

Be aware that strings values built with the greater-than and pipe operators
actually ignore newline characters, therefore no escaping is necessary.

```yaml
do:
   - mydata =: |
         line1
         line2

   # this is the same as above, but no escaping needed
   - lines =: |
       {{ mydata.split('\n') }}

   # same here with a do:, no escaping is necessary:
   - lines = do: |
         mydata.split('\n')
```

### The Difference between `>` and `|`

The greater-than operator `>` will slurp all lines as a single line.

The pipe operator `|` will maintain the newline character at the end of each line.
