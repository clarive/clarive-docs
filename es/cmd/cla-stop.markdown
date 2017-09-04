---
title: cla stop - Detiene todos los procesos
index: 5000
icon: console
---

`cla stop`: Detiene todos los procesos del servidor. Esto es, intentará detener todos los sistemas que Clarive necesita
para operar.

Estos son:

- *mongo*: Detiene el servidor de Mongo.
- *nginx*: Detiene el servidor nginx.
- *Clarive web server*: Detiene el servidor web.
- *Clarive dispatcher*: Detiene el dispatcher.

El comando admite los siguientes parámetros:

- `--no_mongo`: Detiene todos los procesos salvo los relacionados con el servidor de Mongo.
- `--no_nginx`: Detiene todos los procesos salvo los relacionados con el servidor de nginx.
