---
title: Calendaring - When can a Job run?
index: 550
---

Clarive continuous delivery is as much about letting teams release their changes whenever they deem them to be ready, as
it is about letting the organization plan and execute a carefully organized delivery process.

The Clarive Calendaring System sits in the middle between these two approaches or speeds, working as the arbiter between
the organizational requirements and the agility of teams working around the clock to compete.

Not all Jobs can run whenever they are scheduled. There are external constraints to be observed, which is key to
*avoiding disruption* to applications and services being delivered.

Clarive jobs can include automated and manual deployment and provisioning tasks. Therefore, plan your calendar slots
carefully to prevent both deployment and provisioning tasks at a given time:

- Environment Calendars.
- Nature (technology) Calendars.
- Project Calendars.
- Calendar for other Resources.

### Weekly Plan

Clarive calendars follow a seven-day layout that repeats weekly.

There can also be specific slots for specfic dates, such as holidays.

### Slot Types

There are four slot types:

- `Empty` - no slot has been defined, so no Jobs can run.
- `Normal` - normal deployment slot.
- `Urgent` - urgent deployments only.
- `No Job` - no Jobs can run during this slot.

The difference between `Empty` and `No Job` is the way they act in a merge. See below for more details.

### Global Calendar

The Global Calendar is the default calendar that will be used in the event that no other calendar matches.

### Environment Slots

These are the simplest calendars to set up.

Create one calendar per environment in the system. This is not mandatory, although it may be best to start with one
calendar per environment. Morevover, this will make it easier in the future, should you plan to have different calendars
for at least one environment.

If no environment calendars have been set up, then the Global Calendar will be applied.

### Calendar Merge

Let us suppose Release 2.0 is going to deploy two different projects into the Production Environment, projects A and B.

Project A only allows scheduling of jobs to PROD after 10pm.

Project B has a similar constraint, but after 11pm.

If you try to schedule Release 2.0 to deploy to Production, the first slot available will be 11pm. That is because
Clarive **intersects** slots restrictively to determine which is the next available slot.

Implementation guidelines:

- Set merge priorities for every calendar you create.
- Only use `No Job` if you want to block the slot at a high-precedence slot.

#### Precedence

The calendar precedence sets the order in which merge is applied. A higher precedence means it is more *important* than
lower precedence numbers.

If two slots have the same precedence, the precedence will be defined by the alphabetical order of each calendar name.

#### Wildcard Slots

The `Empty` slot is a wildcard slot, and even a higher precedence slot that is `Empty` can be filled with data from
lower precedence.

Use `Empty` to denote that deployment could take place at a given time if needed by any calendar. Use `No Job` to
effectively deny deployment for higher precedence Jobs.

### Calendaring Constraints Through Rules

You can also prevent a Job from running by putting a control checking during a pipeline rule `CHECK` step.

For example, you could check the existence of a file in a directory in the Clarive server to prevent a Job from being
created. Simply fail (use the `FAIL` op) during the `CHECK` step to prevent a Job from being created.

#### Outward Calendaring Integrations

The rule can also call other tools for checking Calendaring constraints during the `CHECK` step of the rule.
