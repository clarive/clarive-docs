---
title: Cargar Tópicos Relacionados
index: 5000
icon: service-topic-condition
---

Este servicio carga en el stash a través de una variable la información de uno o varios tópicos que estén relacionados
con un tópico específico.  La variable se define en el campo `Clave de retorno` de la pestaña `Opciones`.

En el formulario del servicio se pueden configurar los siguientes campos:

- **Nombre** - Permite al usuario cambiar el nombre del servicio.
- **Mid** - El tópico desde el cual se quieren cargar los tópicos relacionados. Permite el uso de variables (ej:
${my_changeset} o en caso de que el changeset se encuentre en el stash: ${changesets[0].mid} ).
- **Tipo de relación** - Indica el tipo de relación que guardan los tópicos que se quieren cargar y el tópico indicado
en el campo anterior.
- **Filtrar estados** - Filtra por los estados seleccionados los tópicos relacionados.
- **Excluir de los estados** - Hace que el filtro por estado se aplique de forma inversa. Se excluirán los estados
indicados en `Filtrar estados`.
- **Filtrar categorías** - Filtra por las categorías seleccionadas los tópicos relacionados.
- **Profundidad** - Limita el grado de búsqueda de tópicos relacionados. Por ejemplo, una profundidad de 2, cargará los
tópicos padre (nivel 1) y los tópicos padres de éstos (nivel 2). No es recomendable el uso de un valor elevado.
- **¿Único?** - Actívalo si sólo quieres que se cargue el tópico relacionado con `Mid` más bajo (utiliza filtros para
acotar la búsqueda).
- **No excluir el mid del evento** - Si está activo, también carga en la variable los datos del tópico indicado en
`Mid`.
- **¿Sólo mids?** - Actívalo si sólo quieres cargar en el stash el `Mid` de los tópicos relacionados. En casos
concretos, es conveniente activar esta opción para evitar cargar toda la información de los tópicos en el stash.
