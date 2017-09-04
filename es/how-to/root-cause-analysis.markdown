---
title: Crear Análisis de causa raíz
index: 5000
icon: page
---

El [Análisis de causa raíz](/concepts/root-cause-analysis) es un método para la resolución de problemas identificando
las causas del mismo. Para realizar un análisis hay que seguir los unos sencillos pasos.

Primero hay que añadir un demonio nuevo *service.root_cause_analysis.daemon* en la sección de [Demonios](/admin/daemon).
Una vez añadido y activado, es necesario crear un Recurso de tipo 'Root Cause' donde se definirá el nombre del Recurso,
la severidad, una interpretación del problema (un titular), una guía (donde se detalla más extensamente el problema)
y una expresión regular, donde se define con qué mensaje del sistema saltará este Análisis de Causa Raíz.

Por ejemplo, crearemos un Análisis de causa raíz para cuando, al enviar un fichero de manera remota, falla la conexión
a la maquina destino.

Primero definimos el Recurso:

- **Nombre** - Conexión perdida
- **Severidad** - Alta
- **Interpretación** - Se ha perdido la conexión.
- **Guía** - No se ha podido establecer la conexión con la maquina remota. Compruebe que los datos del servicio son
  correctos, que la maquina dispone de conexión a Internet y de que el cortafuegos está desactivado.
- **Incluir** - could not connect

A continuación, indicamos en que servicio de la regla se activará el análisis.  Para ello, accedemos a la regla,
y accedemos a las [propiedades del servicio](/rules/rule-palette) (click derecho sobre el servicio y pulsamos en
Propiedades). Al abrirse las propiedades aparece una pestaña "Análisis de Causa Raíz" con un combo donde se especifica
el Recurso.

Una vez configurado estos tres elementos (demonio, Recurso y servicio) ya tenemos el análisis preparado. Cada vez que en
el log del pase se muestre la expresión regular indicada en el Recurso (*could not connect*) se mostrará la información
del Recurso; la severidad, la interpretación y la guía. Este análisis se muestra tanto en el Resumen del log como en el
log detallado. Si no aparece en el log detallado, asegúrese que tiene configurado la ventana para que muestre los
mensajes de Debug.
