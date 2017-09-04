---
title: Monitoring Jobs
icon: television
index: 1000
---

The Clarive [Job](/concepts/job) Monitor keeps track of all jobs running in the system in a single, integrated
interface.

Each job shown in the monitor links to both their Job Dashboard and Job Log interface, for extensive detail on what is
being run by the job.

## Monitor Fields and Data

#### Job Statuses

Here's a list of job statuses and their meaning:

- `Ready` - Job is waiting to be picked-up by the [job daemon](/admin/daemon), which can happen at any moment, except
  for the `RUN` step, which runs at a scheduled date.
- `Running` - Job is currently running
- `Waiting for Approval` - Waiting for an approver to approve or reject the job in the monitor.
- `Rejected` - Approver has rejected the job. Job is at a stand-still and won't be run unless action is taken.
- `Expired` - The current date and time is greater than the `Max Start Date`, so the job `RUN` step has been canceled
- `Abend` - The Job Daemon could not find the job process on the server, so it's marked as an aborted (crashed or
  killed) process
- `Rollback` - Job is running a rollback operation
- `Finished` - Job finished running
- `Error` - Job finished with an error at any of its steps
- `Canceled` - Job was canceled by a user while it was running
- `Trapped` - An error was trapped and it's waiting for user input
- `Trap Paused` - User has decided to pause the trap timeout counter since a longer resolution time is expected.

Always check the `Step` column to get a sense of where the job is at a given point in time.

#### Job Steps

Job steps indicate which phase of the job is being run (or expected to be run) by the job daemon at a given time.

- `CHECK` - This step is previous to a job being created in the database and is not visible in the monitor
- `INIT` - Job has just been created, but the user is still waiting for confirmation. This is actually visible in the
  monitor
- `PRE` - During this step, the job will run all preparation that does not affect target environments, such as building
  an application or running tests.
- `RUN` - This step contains the rule logic that is going to run during the scheduled time.
- `POST` - This is the final step in the job pipeline chain. This step runs in the event of success or failure after
  a `PRE` or `RUN`steps

#### Job Progress

Progress is calculated by counting the number of total ops against the ones that have run. It does not include any loop
unrolling, so the progress may not be 100% accurate, but gives an idea of how far the job pipeline has advanced.

#### Job Natures

Once the job contents are determined, Clarive parses all revisions and determines which natures are included.

So, this information is not necessarily available after job creation, but only after the `PRE` step runs.

#### Job Dates

- `Start Date` - The real date-time that the job started its `PRE` step.
- `End Date` - The real date-time when the job reached its `END` step.
- `Scheduled` - This is when the `RUN` step is planned to run.
- `Max Start Date` - If the job does not start by this date, it is marked as `Expired` automatically by the job daemon.

## Monitor Actions

With the job monitor, you can control what happens to each job running, such as starting, canceling, deleting, reruning,
etc.

These actions also require that the user have the adequate permissions, discussed further down this section.

### Rerun

Rerun allows a job to be put in `Ready` status for a given step.

Normally, jobs are either rerun for `PRE` or `RUN` steps, to repeat things like build or deploy phases.

Also `POST` steps may be run for redoing things like resend notifications or promotions.

**NOTE**: If you rerun a step, all following steps will also be rerun, with the following behavior:

- If a `PRE` step is rerun, the `RUN` step still will preserve and wait for its scheduled date to be run.
- If a `RUN` step is rerun, the scheduled date can be overruled with the `Run Now` option.

### Reschedule

Jobs that are in `Ready`, `Expired` or `Waiting for Approval` can be rescheduled, which means setting a new date for the
`RUN` step to start.

### Job Expiration

Jobs expire automatically when its `Scheduled Date` is greater than their `Max Start Date`.  The purpose of expiring
jobs is to prevent them from start a deployment beyond a system outage, in a off-time.

##### Handling Expired Jobs

If a job has expired, it is not going to run. But using the monitor actions, the operator has 2 options:

- Rerun the job at either `PRE` or `RUN` steps
- Reschedule the job for another time

### Canceling Jobs

Jobs in a `Running` state can be canceled. That will terminate the job immediately in the Clarive server, but **does
not** prevent processes running.

### Permissions

- `action.job.view_monitor` - Has access to see jobs for the authorized scopes in the Job Monitor
- `action.job.approve_all` - Approve any job, even if not in the approval list
- `action.job.restart` - Rerun a job
- `action.job.cancel` - Cancel a job
- `action.job.delete` - Delete a job
- `action.job.create` - Can create a job
