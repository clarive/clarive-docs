---
title: Event Rules
icon: rule
index: 1000
---

An event rule is a rule meant to be fired by a Clarive system event.

When creating the event rule, select the event that's going to trigger your
rule. You can only select one event for each rule. If you want to run the same
logic for more than one event, put that login in an independent rule then
create several events for each rule.

The next step is to select when your event rule will be fired, if before or
after the event happens.

## Event Types

There are 3 event types available:

- Pre-Online
- Post-Online
- Post-Offline

### Pre-Online

A pre-online rule will run before the action that triggered
the event occurs.

If the event is a user event (ie. 'Topic Change Status'),
the user will have to wait for the rule to run before the results are known.

Pre-online rules are ideal to prevent an action, checking values and reporting them
back to the user.

### Post-Online

Post-online events will be triggered immediately after the associated event
action executes.

Post-online events are ideal for running rules that require that the
object created by the action exists, say, a topic, a job, a user, etc.
But only if we really need for the user to wait for the rule to
complete before regaining control over the system.

Typically post-online events are excellent for filling automated
topic form fields for the user. That way the user will get the
results streamlined after her action runs.

!!! warning
    **Use online events sparingly**. They will force your users to wait on your
    rules to run, giving them the feeling that the system is slow and
    preventing users from working. Whenever possible use post-offline rules
    and keep your users happy.

### Post-Offline

Post-offline events will be triggered after the associated event
action executes by an event queue (the event daemon started by the
Dispatcher).

Clarive does not guarantee that the event will be triggered at a specific time.
It may take maybe milliseconds or even a few minutes until the event is picked
up by the queue, depending on the amount of event work queued.

Post-offline rules are ideal to kickoff continuous integration or
deployment jobs, provisioning rules or anything a little bit more complex.

#### Restrictions

When the event is of type `Modified Topic Field` (`event.topic.modify_field`),
the rule will only be executed in the pre-online mode.

### Scopes

When the rule is an event of topic type, the user can assign filters to the
execution of the rule. The three possible filters are:

- _Projects_ - Select the projects which we want to launch the rule. If none is
  specified, the scope works using all projects.
- _Categories_ - Select the categories which we want to launch the rule. If
  none is specified, the scope works using all categories.
- _Statuses_ - Select the statuses which we want to launch the rule. If none is
  specified, the scope works using all statuses.
