---
title: cla/config - Usar variables de configuración
---

En Clarive config podrá cargar las variables de configuración para ser usadas en Clarive.

## config.get()

La opción *get* le permitirá cargar la variable o variables de configuración en una estructura hash. Cargará las
variables de configuración de la clave que se le especifique.

```javascript
var config = require("cla/config");

// This will get the config.test. It can contain just one variable or more.
var config_test = config.get("config.test");

// This will get the value of config.test.variableOne.
var variableOne = config_test.variableOne;
```
