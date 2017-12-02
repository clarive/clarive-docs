---
title: Event Rules
index: 2100
---

You can trigger rules on certain Clarive system events.
These system events can react to these special events
and run automation tasks just like with most other rulebooks.

Using Clarive terminology, Rulebook rules kick-in _post-offline_.  That means
they cannot not interfere with the user action or interact with the user, ie.
if there's an error the user will not see it. These ruleboks are run by the
event daemon as sometimes immediately, sometimes a few seconds later.

In short, this is how an event is processed by the event system:

- user performs action

- system registers event in the queue

- the Clarive `event.daemon` picks up the event in the queue

- if rulebooks that hook in the event exist in the system (checked into the Git
  repositories), the event daemon runs them sequentially.

## Scope of execution

Your rule will only run if the event happens in the project that your rulebook
is defined.

If the project is not present, your rulebook will not run.

## Scope filters

To avoid executing your rulebook for every event in we __strongly recommend__ you
add scope

## topic_create

This event is triggered when a topic is created by a user.

Scope filters:

Scope Key   |  Contents
------------|-----------------------------------
category    | Array of topic category names
status      | Array of topic status names

```yaml

topic_create:
     category:
       - Hotfix
       - Feature
     status:
       - New
       - Done
       - Production
     do:
      - email:
            subject: "Topic {{ ctx.topic().name }} created"
            to: admingroup@example.com
            body: "..."
```

## topic_modify

This event is triggered when any topic field is changed.

Filter scopes:

Scope Key   |  Contents
------------|-----------------------------------
category    | Array of topic category names
status      | Array of topic status names
field       | Array of changed topic fields

If filtered scopes are used, the event trigger will only
run if a given field value has changed.

```yaml
topic_modify:
     fields:
       - title
       - expected_end_date
     category:
       - Hotfix
       - Feature
     do:
       - email:
             subject: "Topic {{ ctx.topic().name }} created"
             to: admingroup@example.com
             body: "..."
```

## topic_delete

This event is triggered when a topic is deleted.

Filter scopes:

Scope Key   |  Contents
------------|-----------------------------------
category    | Array of topic category names

```yaml
topic_delete:
     category:
       - Hotfix
       - Feature
     do:
       - email:
             subject: "Topic {{ ctx.topic().name }} created"
             to: admingroup@example.com
             body: "..."
```
## topic_change_status

This event is triggered when a topic status is changed.

When this event occurs, the topic status has already changed to its new status.

Scope Key   |  Contents
------------|-----------------------------------
category    | Array of topic category names
status      | Array of topic status names

## repository_update

Triggered whenever the current repository (where the rulebook resides) has changes.

## user_register

__This is event only triggers global project events__.

Triggered whenever a new user registers through the registration
page.

## Topic events context functions

The following context functions are available to topic-related
events:

- `ctx.topic()` → returns a hash with properties of the current topic in context
- `ctx.status()` → returns a hash with properties of the current status in context
- `ctx.category()` → returns a hash with properties of the current category in context
- `ctx.fields()` → returns a hash with the modified field old/new data

Head over to the [context calls documentation](/rulebook/context)
for detail on the data returned by each function.
