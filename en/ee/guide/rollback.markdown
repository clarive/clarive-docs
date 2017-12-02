---
title: Rollback and Error Handling
index: 260
---

Clarive keeps track of what has been deployed so far and can roll back intelligently to a previous state, by simply
uninstalling technologies and undoing current changes (select `Deploy`, `Monitor`, *Job*, `Rollback`).

Clarive can roll back to every version of every application for any release, for business as well as
configuration/deployment logic.

There are three types of rollback in Clarive:

- Undeploy
- Fail-safe
- Demote (Backout)

#### Undeploy Rollback

*Undeploy* rolls back a Job, in a way that it "uninstalls" any artifacts and changes applied to the Job.

#### Fail-safe Rollback

Rollback is what happens when a Job fails halfway through and the rollback flag is set.

This is a fail-safe mechanism that undoes everything that has been installed when an error is detected during the
deployment phase.

#### Demote Rollback

A Demote is a Topic transition out of an environment.  Demoting topics from a status that is linked to an Environment
will trigger a Backout Job that will execute a *redeploy of the previous versions* of the pertinent artifacts.

A Topic Backout allows rollback only of selected functional components and unwanted changes from an environment.

Demote or Backout rollback is done on a per-release or per-changeset basis, which is a very powerful way to demote
individual logical entities.

For example, a single changeset can be demoted out of QA, which will trigger a rollback of simply the contents of that
given changeset (given there are no dependencies left behind). Clarive will rebuild the QA environment to match the new
situation of the release contents. This is typically used during QA, Pre-production and UAT phases to discard *unwanted
functional changes* without having to rebuild and redeploy the entire application.

## Fail-safe Rollback Intelligence

Clarive implements several failover rollback detection and execution mechanisms that allow the system to keep track of
what has been changed in the destination Environments, so that, in the event of a failure, a fail-safe rollback is
triggered automatically.  This is controlled by a deployment flag called `Needs Rollback`.

### File Shipping Rollback Triggers

This tracking of changes is done automatically every time Clarive runs a ship operation from within a Pipeline Rule.

And every time a file ships correctly, the rollback flag is set and the deployment rollback will be triggered.

### Needs Rollback Field

The rollback flags can be set manually in a rule by choosing `Properties` for a given op, then selecting the `Needs
Rollback` field option that best describes the rollback behavior for the node.

Undeploy rollbacks of an automation job can be done by selecting a Job, as long as there are no subsequent Jobs for the
same component or artifact in that Environment.

### Writing Reversible Rules

Pipeline rules can be executed in a forward or backwards fashion.  This means the same rule can be used for deploying
a new or previous version of an artifact.

#### Run Forward

This op `Properties` flag tells the Clarive rule engine to run this op when going forward (deployment). If not selected,
it will not run in deployment mode.

#### Run Rollback

This op `Properties` flag tells the Clarive rule engine to run this op when performing a rollback. If not selected, it
will not run in deployment mode.

It is useful to skip rule ops when in rollback mode.  Op nodes in the rule tree are flagged with `NO ROLLBACK` when this
option is deactived.

### IF ROLLBACK

The `IF ROLLBACK` control operation exists so that rules can branch into different behavior, depending on whether it is
being deployed forwards or backwards.

This control operation is very useful when, for instance, rollback is actually very particular to that technology and
cannot be "guessed" by Clarive file backup logic.

### Trapping Errors

Use the op `Properties` option `Error Trap` to trap errors and avoid a rollback being triggered by an op failure.

#### No Trap

Errors are not trapped, and a rollback is triggered if there is an error and the needs rollback flag is on for the job.

#### Trap Errors

These pause the job on an error. The job status changes to `Trapped` and user intervention is necessary.

If the trap timeout is set, the rule engine will fail the job and take appropriate action (rollback or just finish with
an error).

#### Ignore Errors

Errors will be ignored (but reported to the log) for this op.  This means no rollback is triggered on error.

#### Grouping Ops and Error Traps

Ops can be grouped by using the `GROUP` control op, or any op that allows nesting.

If the `Error Trap` flag is set at the group level and the user response is set to **Retry**, the whole group is retried
from the beginning.

If the `Error Trap` flag is set at the group level and the user response is **Skip**, then the whole group is skipped.
