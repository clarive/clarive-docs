---
title: Cadena de Proyecto
index: 5000
icon: dashlet-project-pipeline
---

La cadena de proyecto muestra como las releases, los cambios y las revisiones están distribuidos en los diferentes
entornos.

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

#### Excluir las categorías seleccionadas

Excluye las categorías seleccionadas en el punto anterior.

#### Campo Revisión

Especifíca el ID del campo revisión que pertenece a las categorías seleccionadas (este ID debe ser el mismo en todas ellas). Este dato es necesario para visualizar la información en el modo Revisiones.

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
