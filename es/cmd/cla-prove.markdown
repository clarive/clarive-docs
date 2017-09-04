---
title: cla prove - Ejecuta los tests internos
index: 5000
icon: console
---

`cla prove`: Ejecuta los tests internos y comprueba el resultado de los mismos.

Este comando ejecuta ficheros de test localizados en el directorio de test del core y muestra los resultados en
pantalla.

Cada caso de prueba comienza con:

`[start] <nombre_caso_prueba>`

y finaliza con:

`[end] <nombre_caso_prueba> [<duracion_del_test>]`

En caso de error, se mostrará un mensaje de error en rojo.

El comando acepta las siguientes opciones:

- `<directorio_o_fichero>` - Ejecuta solo los test del core que estén definidos en la ruta de
  …/t/<directorio_o_fichero>.
- `--features` - Ejecuta los test de todas las features.
- `--plugins` - Ejecuta los test de todos los plugins.
- `--feature <nombre_feature>` - Ejecuta los test de la feature <nombre_feature>.
- `--plugin <nombre_plugin>` - Ejecuta los test del plugin <nombre_plugin>.
- `--all` - Ejecuta todos los test de features, plugins y core.
