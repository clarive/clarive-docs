---
title: Cadena de Proyecto
index: 5000
icon: dashlet-project-pipeline
---

La cadena de proyecto muestra como las releases, los cambios y las revisiones están distribuidos en los diferentes
entornos.

### Altura en canvas

Define la altura en numero de filas que se le da al dashlet.

El valor de la altura oscilará entre 1 y 4. Donde con 4 ocupará el 100% de la página.

### Anchura en canvas

Establece el ancho que ocupará el elemento en el dashboard.

El valor máximo permitido es de 12 (100% de anchura).

### Frecuencia de autorefresco

Establece el intervalo de tiempo el cual el elemento se autorrefrescará.

#### Modo

- `Releases` - Grupo de releases contenidos en los diferentes proyectos.
- `Cambios` - Grupo de cambios contenidos en los diferentes proyectos.
- `Revisiones` - Grupo de revisiones contenidos en los diferentes proyectos.

#### Entorno

Selecciona los entornos a mostrar o ocultar.

#### Seleccionar tópicos por categorías

Selecciona las categorías que se desean mostrar. Estas categorías sólo pueden ser de tipo cambio.

#### Campo Revisión

Especifíca el nombre del campo revisión.

#### Condición avanzada JSON/MongoDB

Permite añadir un filtro para las filtrar los topicos y/o categorías a mostrar.

#### Etiquetas en las máscaras

Es el texto que se mostrará en cada una de las releases o cambios listados.

Las variables disponibles son:

- `${category.name}`
- `${category.acronym}`
- `${category.color}`
- `${topic.mid}`
- `${topic.title}`
- `${topic.[field name here]}`
