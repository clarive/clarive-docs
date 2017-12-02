---
title: Rulebook Flow Control
index: 300
---

## If-then-else

Rules can contain `if` ops that execute conditional statements.

```yaml
do:
  - res = shell: curl http://myserver
  - if: "{{ res.rc > 0 && res.rc < 128 }}"
    then:
       - fail: invalid server
       - if: "{{ /resolve/.exec( res.output ) }}"
         then:
           - echo: "a DNS error maybe?"
         else:
           - echo: 'something else then'
```


## Foreach Loops

Foreach loops are meant to run a `do` block over data or the contents of an
array variable using the `foreach` statement.

```yaml
do:
   - foreach:
         var: server
         in:
            - server1
            - server2
         do:
            - curl -LO http://${server1}/test_url
```

The same can be accomplished with variables:


```yaml
vars:
   - servers:
        - server1
        - server2
do:
   - foreach:
         var: server
         in: ${servers}
         do:
            - curl -LO http://${server1}/test_url
```

Note that the `var` argument, which holds the name of the variable that's
receiving each of the values in the `in` array, is a simple string, without any
variable template markers such as `${ }` or `{{ }}`, while the contents of the
`in` arguments need to be resolved.

## Anonymous Foreach loops

You can also use a quicker notation for Foreach loops, without defining an
assigment variable. In that case, the special `it` variable will be set with
the looping value.

```yaml
do:
  - foreach: [ 'server1', 'server2' ]
    do:
       - curl -LO http://${it}/test_url
```

## While loops

You can also build loops using inline ClaJS code.
This is useful for complex loop validation.

```yaml
do:
    - ok =: false
    - while: "{{ ! ok }}"
      do:
         - res = shell: curl -LO http://${server1}/test_url
         - ok =: "{{ res.rc == 0 }}"
```

You can use `while` loops to loop through a counter:

```yaml
do:
  - ok =: '{{ 0 }}'   # yaml values are not numeric, use JS to assign as Int
  - while: "{{ ok < 100 }}"
    do:
       - echo: ${ok}
       - ok =: "{{ ok + 1 }}"
```

## Return

The `return` op exits the current `do` block. You can nest `do` blocks inside `do`
blocks for better flow control, or better, use `def` to define clearly scoped
functions.

Make sure to use a bare `return:` (followed by colon) if no return value supplied,
otherwise it will be executed as a local shell command in a Docker container.

```yaml
do:
  - echo: lets try something
  - do:
      - res = shell: curl http://myserver
      - echo: "Exit code was ${res.rc}"
      - if: '{{ res.rc > 0 }}'
        then:
          - echo: 'we are out of here'
          - return:
      - echo: "everything looks good, so continue"
```


## Fail

To exit the current program, you can also call `fail:`.
This will throw an error up the scope, and can only be caught by a
`try-catch`.
