---
title: cla pubsub - Pubsub daemon management
index: 5000
icon: console
---

The Pubsub daemon offers enhanced streaming, notification and real-time messaging performance within Clarive when
configured. In order to activate the Pubsub daemon, see the instructions in [Config Pubsub
daemon](/how-to/config-pubsub).

Run bootstrap to update your libraries:

```bash
cla bootstrap
```

You can then start the daemon in the command line when starting the Clarive web server:

```bash
cla pubsub --env your_environment --port [Pubsub port] --daemon
```

The daemon should now be running for the current Clarive session.
