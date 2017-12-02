---
title: Pipeline Rules
icon: rule
index: 1010
---

A pipeline rule is a rule that deploys changeset contents into
an environment.

The pipeline rule is the core of a [Job](/concepts/job).

Tipically pipeline rules will revolve around the tasks
necessary to change an environment:

- build
- package
- test
- provision
- orchestrate
- deploy

So a pipeline rule should, at least, do one (if not all)
of the previous activities.

The rule can also become the default for a given transition:

- __Promote__ - Promotes a conceptually superior environment, for example from
  pre-production to production.
- __Static__ - Used to redeploy changesets to the same environment they
  currently occupy.
- __Demote__ - Demotes a conceptually inferior environment, for example from
  production (PROD) to pre-production (PREP).

### Job Steps

When a pipeline rule is created, the 5 standard steps are preloaded. They are:

- __CHECK__
- __INIT__
- __PRE__
- __RUN__
- __POST__

#### CHECK

Control whether or not the job should be created in the first place.

During a `CHECK` step the job object not yet available.
There's no job id.

If the `CHECK` step fails, the job is not created and the user will get an
error message window, with the message thrown by the rule, in the web
interface.

#### INIT

The `INIT` step is very similar to the `CHECK` step,
but the difference is that the job object is already
created in the system.

The `INIT` step runs ops in user-time, so the user
will be waiting for the step to complete, just like
with the `CHECK` step.

Throwing errors in the `INIT` step will leave the job
in an `Error` state and it will not run. The
user will get an error message stating that
the job could not be started for the reason
stated in the `FAIL` op.

The `INIT` step should be used for 2 main reasons:

- when it's necessary that a failed
job verification info is logged as part of the job log.

- when we want the user to wait for confirmation
that the job has been created.

!!! warning
    Do not overload the `INIT` or `CHECK` steps with
    complex and potentially slow tasks. While both
    steps run, the user is blocked out in the interface.

#### PRE

The `PRE` step contains ops that will run immediately after
the job is created and the `INIT` step is completed.

This is where activities that do not modify an environment
should run, such as build, package or testing.

Do not put environment changing ops here, like deploying
the app binaries or packages, or restarting servers.

Use the `PRE` step to prepare everything that will be
needed by the `RUN` step of the pipeline to deploy
your application.

#### RUN

This step contains the portion of the rule that will run at the scheduled time.

For pipelines that are not scheduled, the `RUN` step may start immediately
after the `PRE` step. But if the job has been scheduled at a later time, then
the job will pause after the `PRE` step has completed waiting for the schedule
time.  This is shown in the monitor as the status `Ready` of the step `RUN`.

#### POST

The `POST` step is where error control and final execution ops run.
Typical `POST` activity may include:

- moving changesets and other topics to their desired status, like a `Failed` status
- sending email notifications to users
- updating repository branches with tags that indicate what commit
corresponds to which environment.

The `POST` step will always run. This includes the following:

- After a `PRE` step fails
- After a `RUN` step fails
- After a `RUN` step is successful
