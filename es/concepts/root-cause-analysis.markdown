---
title: Análisis de Causa Raíz
index: 5000
icon: page
---

El Análisis de Causa Raíz permite añadir una descripción personalizada a alto nivel de las diferentes operaciones del
pase. En particular, puede utilizarse para ofrecer una explicación más extendida al usuario cuando se produce un error
en el pase.

Para poder usarlo, hay que configurar varias cosas:

1. Crear un [Recurso](/concepts/resource) de Causa Raíz con descripción y los patrones de coincidencia.
2. Todas las operaciones de reglas que se quieran analizar deben configurarse con los Recursos creados anteriormente.
3. El [demonio](/admin/daemon) de Análisis de Causa Raíz tiene que estar en ejecución para procesar los pases.
