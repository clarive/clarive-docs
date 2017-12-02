---
title: Scheduler
index: 5000
icon: clock
---

The Scheduler is an administrator facility for scheduling the execution [rules](/concepts/rule) at set intervals.

It allows to you to plan, enable, disable or run independent rules in the background, at given frequencies or times.

The Scheduler contains the following information:

- **Name** - Name of the task along with the log output.
- **Status** - Current status of the task.
- **Next time** - The time scheduled for the next run.
- **Last time** - Date and time of the last execution of the task.
- **PID** - PID of the last process.
- **Description** - Description of the task.
- **Frequency** - Follow the format (1H - 1 hour, 1D - one day etc.).
- **Day** - Indicates when the task runs only on daily days (indicated by a 1) or every day (indicated by a 0).
- **What** - The name of the rule and the ID to be executed.

### Scheduling Tasks

To schedule a new task, select the `New` button.

The following fields are required:

- **Name** - Name of the task.
- **Rule** - drop-down combo with the independent rules created in Clarive.
- **Date** - Selecting this button will display a calendar field to select the desired execution date.
- **Time** - Default current. Shows the system time and the arrows can increase or decrease the minutes.
- **Frequency** - Format (1H - 1 hour, 1D - one day etc.).
- **Only weekdays** - Checkbox to select if you want to run only on weekdays.

### Running Tasks On Demand

##### ![](/static/images/icons/start.svg) Run now

If you press the `Run Now` button, the service execution will run immediately, regardless of the date of planning. This
option is available irrespective of the task's status.
