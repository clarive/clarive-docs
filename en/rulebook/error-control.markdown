---
title: Error Handling
index: 1000
---

## Handling shell command errors

Shell commands can error out sometimes.
These errors can be caught in many different ways.

If no the shell command is not being assigned to a
variable, the command will interrupt your rulebook:

```yaml
do:
   - exit 99
   - echo: this will not be echoed due to the above error
```

Errors can be suppressed by assigning the command
execution to a variable. In that case, the variable
will hold the return code and error message.

```yaml
do:
  - cmd_result = shell: nonexisting_command
  - if: '{{ cmd_result.rc > 0 }}'
    then:
       - echo: here's the error = {{ cmd_result.output }}
```

Another way shell commands can be caught is with a well-placed `try-catch` op.

```yaml
do:
  - try:
      - exit 99
    catch:
      - echo: caught error = ${error_message}
```

But if you assign the command output to a variable, no error will be thrown,
rendering the `try-catch` useless.

## Throwing errors with `fail`

In certain situations you may want to throw errors in your rule. This can be
accomplished with the `fail` op. The `fail` op will halt the rule and cascade
the failure to an upper scope.

Throwing errors is simple:

```yaml
do:
   - fail: oh my, fail here
```

Be aware that there are different side effects to throwing an error, depending
on the context of the rulebook:

- for a pipeline rule, the current job will fail and remain in an error status.

- for custom form fields, the user will not be able to open the form and will receive
the error message thrown.

Thrown errors can be combined with `try-catch` blocks for better flow control:

```yaml
def:
   myfunc:
      - fail: we failed
do:
   - try:
       - myfunc:
     catch:
       - echo: myfunc failed bad=${error_message}
```
