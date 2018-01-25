---
title: Stored Variables
index: 210
---

You can store variables in the Clarive database with the
variable admin UI.

Database variables can be accessed conveniently with the
`ctx.var(varname)` function through handlebar notation
in your rulebooks.

```yaml
deploy:
   - image: awsdeployer
        environment:
            AWS_SECRET_ACCESS_KEY_ID: "{{ ctx.var('AWS_SECRET') }}"
        do: |
            serverless deploy
```

## Creating and managing variables

Go to `Admin` → `Variables` in the Clarive app to create and manage variables.

When creating a variable, enter the following info:

- `Variable Name` - the name of the variable, which will be the string used
  when retrieving the value with the `ctx.var(varname)` function.

- `Variable Type` - the type, either `text` (plain text) or `secret`. See
  explanation below to understand the difference.

- `Value` - the value to be stored into the variable.

- `Projects` - projects to which the variable will be available. If no
projects are selected, the variable is available for all projects.

- `Environments` - environments to which the variable will be available. If no
environments are selected, the variable is available for all environments.

Variable names are _not_ unique. You can create several copies of
the same variable for _different contexts_.

## Plain text or Secret variables

__Plain text variables__ are stored as clear text and can be easily read
by the user. This is not ideal for storing sensitive information in the
database.

__Secret variables__ on the other hand are encrypted into the database
and cannot be retrieved outside of the rulebook where it's being used.

## Project and environment scopes

Use project and environment scopes to limit variable access to be used only
from certain types of jobs.

## Cloaking and security

Clarive will attempt to cloak secret variable values at all possible output locations
and logs.

Yet, there's no fully guaranteed variable safety, meaning if a user has access
to a given variable and system it could use creative ways to extract the secret
value.  For example, create a file and ship it to a rogue system; or call a
rogue webservice using the value.

!!! warning
    Be wise and use different strategies to secure your systems, including server-only credentials
    and private keys that are removed from prying eyes.

## Global variables and the REPL

To use / test a variable from the REPL, create __a global value (all projects, all environments)__.
That way the variable can be accessed through the REPL, which is ideal for testing values while
developing rulebooks.
