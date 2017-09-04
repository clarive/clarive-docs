---
title: Configurar demonio Pubsub
index: 5000
icon: daemon
---

El demonio Pubsub permite un rendimiento óptimo de transferencia continua, notificaciones y de mensajería en tiempo real
dentro de Clarive cuando el mismo está configurado.

Para activar el demonio Pubsub, hace falta añadir el siguiente código al fichero [YAML](/concepts/yaml) de su entorno.
Para más información sobre este fichero, consulta el articulo de [fichero de configuración de Clarive](/setup/config-file).

Copie el código que aparece a continuación y péguelo dentro del fichero YAML, asegurándose de
establecer *enabled:* a '1', y completar el parámetro *address* con la dirección y el puerto donde se está ejecutando el demonio Pubsub
Dentro del parámetro *headers* se deberá especficiar la dirección ip y el puerto en el que se está ejecutando el servidor de
Clarive.

    pubsub:
        enabled: 1
        address: [dirección Clarive]:[puerto Pubsub]
        headers:
            - 'Access-Control-Allow-Origin'
            - '[dirección Clarive]:[puerto Clarive]'

Consulte [cla pubsub](/cmd/cla-pubsub) para saber como iniciar el servicio.
