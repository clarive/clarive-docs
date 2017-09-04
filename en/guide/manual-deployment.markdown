---
title: Manual Steps in Deployment
index: 220
---

Although deployment is ideally unattended, Clarive allows a deployment job to have a series of manual steps and manual
intervention operations for Dev and Ops where developer and operations can intervene and collaborate.

Here are some of these manual *breakpoints* that can be implemented:

- Approvals
- Pauses
- (Error) Traps
- Annotations
- ChatOps

Read more about manual steps in a release strategy by referring to the release execution strategies in the [Releasing
Guide](/guide/releasing).

### Approvals

Approval is a control mechanism that allows a Job to be put into an approval state **after a step has finished**.

This means approvals can only run after a `CHECK`, `INIT`, `PRE` or `RUN` job steps. Once in an approval state, the Job
will only advance to the next step if the approver has approved the Job.

If an approver does not approve the Job, it will not roll back.

Jobs in an approval state **do not** take up resources. The job hibernates until either approval or rejection occurs.

Remember, approvals can also be set up as part of a (release, changeset) Topic transition.

### Pause

A pause operation puts the Job in a sleep state, waiting for a User with the adequate permissions to resume the Job.

Resume is an operation in the `Job Monitor`.

To set up a pause, add a `Pause` op anywhere in the deployment rule. Pauses cannot be used during the `CHECK` job step,
since this phase occurs at user time *before* the Job has been created.

### Traps

Traps are intended to stop the Job as failure occurs. This topic is covered in the [Rollback Guide](/guide/rollback).
However, traps can be also used for **assertion**, which means a rule can assert if i.e. if a container that has just
been deployed is running.

Traps can be added to assert operations though its op `Properties` right-click menu option.

For example, call a remote command on a target node to verify that the container is up after deployment, and set up
`Fail on Error` mode. Then set up the error trap on this op to prevent rollback of the deployment job at that point in
time.

### Annotations

Annotations are a way in which teams that are following a deployment job can intervene and report results though the Job
log interface in Clarive.

Annotations can contain any of the following:

- User comments.
- Attached files.
- Large log text.
- Miscellaneous.

Annotations can be created at any time during the lifecycle of the job, although typically they are used to manage a Job
while it executes, adding more data to errors, failures and other information.

#### ChatOps

Clarive TalkBack and ChatOps functionality can be used to report back information into the Job before, during and after
its execution.

To open a ChatOps channel for discussing manual activities over the lifecycle of the Job, create a new channel in Slack
with the following command:

    @cla add #job-qa-1234

Where `#job-qa-1234` is the Job ID from the Monitor.

All commands and comments executed within the Slack chat window will be reported back into the Job.

To define authorized commands Clarive can execute, please setup `TalkBack` configuration items in Clarive that associate
actions that the Clarive `@cla` OpBot can execute.
