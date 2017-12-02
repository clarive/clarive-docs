---
title: Independent Rules
icon: rule
index: 1040
---

An independent rule is a rule that is meant to be called from one or more
rules.

!!! tip
    Independent rules are ideal to avoid code duplication.
    Use them abundantly, instead of copy-pasting ops
    from one rule to the next.

Independent rules do not require any previous information. Think of
independent rules as modules or subroutines. They do not affect the system
behaviour unless called from another rule.

### Scheduling independent rules

One the uses for Independent rules is that they can
be scheduled (think "_Unix cron_").

Create an Independent rule than head over to the
[Scheduler](/ee/admin/scheduler) to create a scheduled
task. Select the rule you created in the scheduler
`Rule` drop-down combo.

### Calling independent rules from another rule

Use the `CALL` palette op, under the `Control`
palette group.

!!! tip
    You can open an independent rule by clicking the `CALL` op node in the rule editor.
