---
title: Estados y transiciones
index: 5000
icon: state
---

Un *Estado* es un [Recurso](/concepts/resource) que representa el estado de un elemento (tópico, trabajo, etc.) en un
punto especifico del [Flujo de trabajo](/concepts/workflow). Un elemento puede estar en un único estado a la vez.

Cuando se definen los estados, también se configurar las propiedades de éstos. Este trabajo se realiza a través de la
sección de [Administración de estados](/admin/status).

### Transiciones

Una *transición* es un relación entre dos estados que permiten al elemento a pasar de un estado a otro. Para que un
elemento pueda moverse entre el estado origen y el estado destino, debe estar definida la transición.

Una transición es un flujo de un único sentido, por lo que si el elemento necesita moverse hacia atrás deben de crearse
las transiciones necesarias para ello.

### Tipos de Estados

Hay cinco tipos de estados

- **Nuevo** - Indica que un [tópico](/concepts/topic) justo se ha creado y no ha sido "cogido" por el equipo.
- **Cancelado** - Indica un estado de abortar.
- **Cerrado** - Indica que el estado es probablemente el último del flujo. Al marcar un estado como Cerrado, los tópicos
  con ese estado no serán mostrados en muchas vistas por defecto como el los listados o Kanban.
- **Desplegable** - Significa que, como parte de la transición en ese estado (promoción), los tópicos "Cambios"
  necesitan ser desplegables a al menos uno de los entornos asociados. Como parte de la transición hacia atrás
(devolver), Los tópicos de tipo Cambio necesitan volver desde alguno de esos entornos.
- **Genérico** - Cualquier otros estados que existen en esa categoría.

### Promoción

Las transiciones de tipo promoción en Clarive representan las transiciones a estados desplegables.

### Devolver

Las transiciones de tipo Devolver, por otro lado, generan las transición devueltas, con un [pase](/concepts/job) [marcha
atrás](/concepts/rollback).

### Cómo cambiar el estado de un tópico

Haga click en `Cambiar estado` para desplegar un menú que enumera todos los estados de ciclo de vida disponibles al
tópico actual. Aquí se enumeran en su orden de progresión lógica a través del ciclo de vida del tópico. Cambiado el
estado del tópico, ciérrelo y vuelva abrirlo para mostrar su nuevo estado en cualesquiera de los modos de ciclo de vida.
