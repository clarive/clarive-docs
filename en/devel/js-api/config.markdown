---
title: cla/config - Using configuration variables
---

In Clarive config you will be able to load configuration variables to be used in Clarive.

## config.get()

*Get* option will load the configuration variable or variables into a hash structure. It will load the configuration
variables from the key you specify in it.

```javascript
var config = require("cla/config");

// This will get the config.test. It can contain just one variable or more.
var config_test = config.get("config.test");

// This will get the value of config.test.variableOne.
var variableOne = config_test.variableOne;
```
