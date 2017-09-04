---
title: cla pubsub - Administración de demonio Pubsub
index: 5000
icon: console
---

El demonio Pubsub permite un rendimiento óptimo de transferencia continua, notificaciones y de mensajería en tiempo real
dentro de Clarive. Para activar el demonio Pubsub véanse las indicaciones en
[Configurar demonio Pubsub](/how-to/config-pubsub).

Ejecute bootstrap en la línea de comandos para actualizar sus librerías:

```bash
cla bootstrap
```

A continuación podrá iniciar el demonio a la hora de arrancar el servidor web de Clarive:

```bash
cla pubsub --env su_entorno --port [puerto pubsub] --daemon
```
