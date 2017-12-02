---
title: Dispatcher
index: 5000
icon: daemon
---

The Dispatcher is the Clarive supervisor process
that starts and manages all required daemons.

Typically the daemons managed by the dispatcher include:

- email daemon, which manages email messages

- event daemon, which runs events

- job daemon, which starts pipeline jobs

- purge daemon, which cleans old logs and data from the system
