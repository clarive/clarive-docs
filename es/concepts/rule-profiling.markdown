---
title: Análisis de rendimiento de la regla
index: 5000
icon: rule
---

Un análisis de rendimiento permite controlar y analizar el rendimiento de un pase y de la regla que lo ejecuta. Para
ello se han incluido una serie de medidas que permite controlar los tiempos de ejecución de cada uno de los elementos de
la regla y del pase.

# Configuración

Por defecto, el análisis de rendimiento de la regla no está activado debiado a que puede afectar al rendimiento de la
misma. Dentro de la configuración de Clarive existen las siguientes opciones:

- `config.rules.profiling.ids` - selecciona las reglas por ids
- `config.rules.profiling.types` - selecciona las reglas por tipo.

Para analizar dos o más reglas, los valores deben establecerse separados por comas.

# Regla

En cada uno de los servicios de una regla, se ha incluido una nueva opción que permite ver al usuario el número de veces
que se ha ejecutado un servicio, la media y sus valores extremos, es decir, la ejecución más lenta y la más rápida.

Además se puede ver una gráfica donde se muestran los tiempos de ejecución del elemento en cada una de las ejecuciones.

Para acceder a estos datos basta con hacer click derecho en el elemento deseado, y acceder a sus `Propiedades`. En la
nueva ventana, aparecerá una nueva pestaña **Profiling** donde se mostrarán los valores descritos.

# Pase

Por otro lado, en el detalle de los pases se ha incluido una pestaña nueva donde se observará el tiempo de ejecución de
cada uno de los elementos de la regla que han intervenido en el pase. Clarive mostrará una gráfico circular con el
tiempo que ha tardado cada uno de los elementos.

Además, en la parte inferior, se muestra una tabla con las operaciones ejecutadas en el pase y sus diferentes tiempos:

### Paso

Muestra los pasos del pase.

### Operación

Muestra las operaciones que se han llevado a cabo. En ellas también aparecerá entre paréntesis el tipo de operación que
se realiza y que luego es reflejada en el gráfico superior.

Además, se muestra una primera fila *idle* que indica cuanto tiempo ha estado el pase esperando.

### Media

Muestra el tiempo medio de la operación. Si la operación se ha ejecutado una sola vez mostrará el tiempo que ha tardado
en ejecutarse.

Sin embargo si la operación está dentro de un bucle y se ha ejecutado más de una vez, se mostrará el tiempo medio que ha
tardado en ejecutarse.

### Ejecuciones

Muestra el número de ejecuciones de la operación.

### Tiempo Exclusivo

Muestra el tiempo que ha tardado la operación en ejecutarse.

### Tiempo inclusivo

Muestra el tiempo que ha tardado en ejecutarse la operación y sus operaciones anidadas.
