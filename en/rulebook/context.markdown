---
title: Context Data
index: 950
---

Rules mostly execute within a context, such as webhooks, topic events or pipelines.

To use the data that triggered the context, there's a ClaJS namespace called `ctx`
that is always available to rulebooks.

Context Function             | Context            | Data Type   |  Contents
-----------------------------|--------------------| ------------|------------------------------------------------------
`ctx.category()`             | any topic event    | Object      | Category information
`ctx.fields()`               | topic_modify       | Array       | List of changed fields, with old and new value
`ctx.job()`                  | pipelines          | Object      | Job information
`ctx.env()`                  | pipelines          | String      | Current job environment
`ctx.branch()`               | pipelines          | String      | Name of the branch checked out for the job
`ctx.request()`              | webhook            | Request     | Web request parameters
`ctx.status()`               | any topic event    | Object      | Status information
`ctx.topic()`                | any topic event    | Object      | Topic information
`ctx.user()`                 | (any)              | String      | User id

!!! info "`undefined` when not in context"
    When not in context, all context functions will return
    `undefined` and emit a warning to stderr `[warn] X not in context`.

    Make sure to check the return value or use `ctx.has()` before proceeding
    under the assumption that the return value is a hash `{}`

## Usage

Context calls are useful to the detail of the event the rule is processing:

```yaml
topic_modify:
   - echo: "Topic modify event for {{ ctx.topic("name") }}"
   - echo: |
        These fields have changed: {{ ctx.fields().map( function(field){ return field.field } ) }}"
```

## Context Objects

These are the context objects available in Clarive.

Remember, if you are not in the correct context, they will return `undefined`
instead of a hash `Object`.  Use `ctx.has()` to check the context, otherwise
strange side effects may happen.

#### ctx.topic()

This is the hash returned by the `ctx.topic()` ClaJS function.
The hash has the following keys:

Key                                       | Context
------------------------------------------|--------------------
`ctx.topic("mid")`                        | topic id
`ctx.topic("title")`                      | status name string
`ctx.topic("status")`                     | status name string
`ctx.topic("category")`                   | category name string
`[category dependent fields]`             | additional fields, depending on the category

```yaml
do: |
   print( "Topic ID=" + ctx.topic("mid") );
   print( "Topic Title=" + ctx.topic("title") );
   print( "Status name=" + ctx.topic("status") );      # "To Do", "In Progress", etc.
   print( "Category name=" + ctx.topic("category") );  # "Bugfix", "Feature", etc.
```

Head over to the [document on event rules](/rulebook/events) for more info.

#### ctx.fields()

The `ctx.fields()` context function returns a list (array) of modified fields in the
`topic_modify` event.

Here's a list of fields available:

Key               | Type          | Description
------------------|---------------|------------------------------------------------------
`field`           | string        | Field name (ie. "title", "description", etc)
`old_value`       | (variable)    | Field value _before_ change. Type depends on field.
`new_value`       | string        | Field value _after_ change. Type depends on field.

#### ctx.job()

Here's a description of the hash returned by the `ctx.job()` function:

Key                          | Type          | Description
-----------------------------|---------------|------------------------------------------------------
`ctx.job("project")`         | String        | Current project being processed, if any
`ctx.job("change_version")`  | String        | Version id from the Release topic, etc.
`ctx.job("environment")`     | String        | Current deployment environment (DEV, QA, PROD...)
`ctx.job("items")`           | Array         | List of job items
`ctx.job("name")`            | String        | Job name (as shown in the Monitor)
`ctx.job("type")`            | String        | `static`, `promote` or `demote`
`ctx.job("user")`            | String        | User that created  job
`ctx.job("mode")`            | String        | `forward` or `rollback`
`ctx.job("step")`            | String        | current job step: `CHECK`, `INIT`, `PRE`, `RUN`, `POST`
`ctx.job("status_from")`     | String        | Current project being processed, if any
`ctx.job("status_to")`       | String        | Version id from the Release topic, etc.
`ctx.job("is_rollback")`     | String        | Current deployment environment (DEV, QA,

#### ctx.request()

The web request context is only available in [webhook url call events](/rulebook/webhooks).

Key                            | Type          |  Contents
-------------------------------|---------------|------------------------------------------------------
`ctx.request('params')`        | String        | The URL query-string or form params in a hash
`ctx.request('args')`          | String        | Array with each of the `/path` components of the URL
`ctx.request('body')`          | String        | The full request body as a string
`ctx.request('headers')`       | Object        | HTTP request headers
`ctx.request('upload')`        | String        | Uploaded files
`ctx.user()`                   | String        | The user id who made the (authenticated) request

#### Checking if context is available

If the context is not available, trying to use the `ctx` context functions will generate
an error such as:

    context `CONTEXT_NAME` is not available

To check before using a function, use the `ctx.has('context_name')` function,
which returns `true` or `false` depending on the context.

This is specially useful for ops defined with `def:`. That way one can check if
the op is in the correct context or not.

```yaml
def:
   reset_topic_title:
      - if: "{{ ctx.has('topic') }}"
        then:
          - update_topic:
                mid: ${mid}
                data:
                   title: "The new title is this now"
        else:
          - fail: "No topic available in context"
```

This is the list of arguments one can test the context with `ctx.has()`:

- `topic`
- `status`
- `category`
- `job`
- `fields`
- `request`
- `user`
