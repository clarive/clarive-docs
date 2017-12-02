---
title: Config Pubsub daemon
index: 5000
icon: daemon
---

The Pubsub daemon offers enhanced streaming, notification and real-time messaging performance within Clarive when
configured.

In order to activate the Pubsub daemon, you need to add the necessary code to the [YAML](/concepts/yaml) file that you
call when starting the Clarive web server. You can find details of this file in the [Clarive configuration
file](/setup/config-file).

Copy the following code and paste it into the aforementioned YAML file, being sure to set *enabled:* to '1', and change
[Clarive address] for *address:* to the IP address you use to access Clarive, and [Pubsub port] to a free port (your
system administrator will provide this number). [Clarive address] and [Clarive port] in *headers:* should be the same as
those used when accessing Clarive:

    pubsub:
        enabled: 1
        address: [Clarive address]:[Pubsub port]
        headers:
            - 'Access-Control-Allow-Origin'
            - '[Clarive address]:[Clarive port]'

In order to start the service see [cla pubsub - Pubsub daemon management](/cmd/cla-pubsub).
