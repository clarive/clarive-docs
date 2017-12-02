---
title: Daemons
index: 5000
icon: daemon
---

A daemon is a computer program that runs as a background process, rather than being under the direct control of an
interactive user.

In Clarive, daemons are special, independent background processes started by the [Dispatcher](/ee/admin/dispatcher).

Daemons are critical to the correct operation of Clarive, including:

- [Job](/concepts/job) execution
- Event processing
- [Notifications](/ee/admin/notifications)
- [Scheduled](/ee/admin/scheduler) executions.
- Semaphore control

Accessing the *Daemon* administration in the Admin - ![](/static/images/icons/daemon.svg) Daemons

In the *Daemons* screen, we can see what daemons are active at a given point in time.

These are the standard, out-of-the box daemons that should be running in any typical Clarive installation.

- `service.daemon.email` - Daemon responsible for sending notifications.
- `service.event.daemon` - Daemon responsible for the management of events.
- `service.job.daemon` - Daemon responsible for the execution of passes.
- `service.purge.daemon` - Daemon responsible for the purge.
- `service.schedule daemon` - Responsible for planning.
- `service.sem.daemon` - Daemon responsible for controlling traffic lights.
- `service.root_cause_analysis.daemon` - Daemon responsible for Root-Cause Analysis (See [Root-Cause
  Analysis](/concepts/root-cause-analysis)).

### Options

If at any time it is preferred that a particular service not be run, for example the purge daemon, we can disable it
from this screen.

Actions associated with the buttons on the toolbar:

- ![](/static/images/icons/add.svg) **Create** - Create new daemon attached to the Dispatcher.
- ![](/static/images/icons/edit.svg) **Edit** - Modify the configuration for existing daemons.
- ![](/static/images/icons/delete.svg) **Delete** - Delete an existing daemon.
- ![](/static/images/icons/start.svg) **Start** - Run a daemon that has been stopped.
- ![](/static/images/icons/stop.svg) **Stop** - Stop a running daemon.
