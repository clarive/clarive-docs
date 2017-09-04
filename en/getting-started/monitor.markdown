---
title: Monitor
index: 5000
icon: television
---

The Monitor shows the list of [Jobs](/concepts/job) that have been created, together with their Status.  You can change
how the names appear in Monitor by modifying the variable *config.job.mask* [Config Job Mask](/how-to/config-job-mask).

The following action buttons are available above the Jobs list:

![](/static/images/icons/logo-html.svg) **HTML** - Shows the log of the Job selected in HTML format.

![](/static/images/icons/project.svg) **Project** - Filters the Jobs by Project.

![](/static/images/icons/ci-bl.svg) **Environment** - Filters the Jobs by [Environment](/concepts/environment).

![](/static/images/icons/nature.svg) **Nature** - Filters the Jobs by Nature.

![](/static/images/icons/state.svg) **Status** - Filters the Jobs by [Status](/concepts/status).

**Type** - Filters the Jobs by type.

![](/static/images/icons/job.svg) **New** - Creates a new Job.

![](/static/images/icons/job-full-log.svg) **Full log** - Shows the log of the selected Job.

![](/static/images/icons/delete.svg) **Delete** - Deletes the selected Job.

![](/static/images/icons/left.svg) **Rollback** - Run the [Rollback](/concepts/rollback).

![](/static/images/icons/job-restart.svg) **Rerun** - Start the Job again from the Step specified by the User.

![](/static/images/icons/datefield.svg) **Reschedule** - Modify the schedule of the Job. This action is only available
when the Status of the Job is *Ready* or *Waiting for Approval*.
