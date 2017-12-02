---
title: Semaphores
index: 5000
icon: semaphore
---

The Semaphore interface is where administrators can manage all semaphores
created in the system.

If a part of a rule or rulebook has been tagged with the semaphore, the
semaphore entry will be created in the system. Every time the rule code
execution enters the semaphored region, it will request exclusivity before
executing the op (and any children ops).

## Creating a semaphore with the REPL

Initially, when no semaphores have been yet created by any
rule, the interface will contain no data. Run a rule
with an that has a semaphore configured to initialize
a semaphore entry.

An easy way to initialize a semaphore is to head over to the
[REPL](/concepts/repl) and run the following JS Server code:

```javascript
var sem = require("cla/sem");
var util = require("cla/util");
var ret = sem.take('mysem', function(){
    util.sleep(10); // will lock the semaphore for 10 seconds
});
```

## Managing slots

Once a semaphore is created, they will visible in the Semaphores
admin panel.

Each semaphore defined in the system will be visible on the left side, the Semaphore explorer.
For each semaphore, the following fields will be shown:

- __slots__ - the number of slots available. This can be increased or decreased with
the up/down arrows next to the semaphore name. Default is `1`, which means only one
process can use the semaphore at once.

- __busy__ - this is the number of taken slots. Default is `0` which means no
process is using any slots. Busy can only

- __waiting__ - number of enqueued processes waiting for available slots.

### Increasing available slots

Semaphores by default do not allow simultaneous executions.
However, the number of concurrent executions allowed can be increased
by using the up/down arrows next to the semaphore name.

!!! note
    Lowering the number of available slots once
    they are already taken won't have any effect on ongoing processes,
    only on new incoming semaphore requests.

### Global semaphore lock

Setting the number of slots to `0` will force enqueuing of all processes
that use that semaphore.

This is an elegant way of preventing users and processes from accessing a process
for a certain amount of time.

### Infinite slots

If the number of slots is lowered (down arrow) beyond `0`, _infinite_ slots
will be available and an infinity sign `∞` will be shown. That translates into
disabling semaphore control entirely.

## Live semaphore management

Once a process is either queued to take a semaphore, or
is busy within a semaphore section, the process will be visible
as a row in the right side panel.

Each row has an icon that indicates the status of the process:

Icon                                            | Status    | Meaning
------------------------------------------------|-----------|----------------------------------------
![](/static/images/icons/busy.svg)              | waiting   | process waiting for an available slot
![](/static/images/loading/loading-fast.gif)    | busy      | semaphore taken and process running
![](/static/images/icons/stop.svg)              | cancelled | process was cancelled on request

There are more statuses, visible in the `Legend` reference in the lower part of the panel,
but usually they are ephimeral in duration and either should not be visible most of the time
or will last a fraction of a second until it disappears from the list.

There are 2 actions available for each row:

- __Grant__
- __Cancel__

### Grant

Grant is meant to release enqueued processes -- processes waiting for a semaphore.

This action ignores the slot restriction, skipping over it entirely.

For instance, say you have a single slot semaphore X and the following process queue:

Process | Status
--------|-------------
   A    |  busy
   B    |  waiting
   C    |  waiting

In the above example, process B is waiting in queue for A to release semaphore X.

If you __grant__ process B, it will start immediately _and will not consume any
slots_. Once process A finishes, process C will start _even though process B is
already running_.

The cancel action is meant to resolve critical queue situations, mostly for emergency
situations where process B must run immediately regardless of slot availability.

### Cancel

The Cancel action will tell the waiting process to fail.

This is meant to prevent processes in the queue from taking semaphores and failing
gracefully with a `Semaphore cancel` error.

Cancelling processes in the queue can be useful in situations where a critical
external resource (ie. a server) is blocking or too slow and requires manual
intervention from administrators before any other process interacts with it.

In the above case, for instance, administrators should:

1. reduce the semaphore slot count to `0`

2. cancel any pending processes in the queue.
