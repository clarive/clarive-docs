---
title: Config Table
index: 5000
icon: page
---

The *Config Table* is where global __dynamic__ configuration settings are stored in the Clarive database.

*Dynamic configuration* settings are settings that can be changed at any moment by an administrator. Through these,
changes will be take effect instantly within Clarive.

This is precisely what makes these configuration values different from the *static* configuration settings that are set
in the [configuration files](/setup/config-file). Static values require a server or [dispatcher](/ee/admin/dispatcher)
restart.

For example, the following are examples of global dynamic configuration variables that can be set through the config
table:

    config.daemon.purge.frequency: 86400
    config.git.path: /opt/repository
