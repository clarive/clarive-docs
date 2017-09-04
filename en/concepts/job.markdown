---
title: Job
index: 5000
icon: job
---

*Jobs* are [rules](/concepts/rule) executed by the Clarive server.

Jobs are always scheduled, regardless of whether they are scheduled to run **now** or in three months' time, they always
have a schedule and are run by the Job [daemon](/admin/daemon).

Jobs can be executed many times through [reruns](/concepts/rerun).

Unlike *Jenkins*, jobs are not a statically scheduled entity. You cannot schedule repeateable jobs. Jobs are
*schedule-once* and *run-once* (even though you may manually reschedule or rerun them as many times as you like).

If you wish to schedule a job to run frequently (i.e. daily, nightly, every two days...), use the
[Scheduler](/admin/scheduler) facility.

When you create a new job, the available pipelines will be the rules that the [project](/concepts/project) of the
changeset has associated and only if they are actived.

## Job are Resources

The Job name identifies the Job. But Jobs are also Resources and therefore have a [MID](/concepts/mid).
