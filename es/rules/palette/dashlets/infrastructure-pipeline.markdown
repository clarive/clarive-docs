---
title: Infrastructure Pipeline
index: 5000
icon: dashlet-pipeline-infrastructure
---

La cadena de proyecto muestra como los recursos de las releases, los cambios y las revisiones están distribuidos en los
diferentes entornos.

Estos recursos se definen creando variables de tipo recurso y asignandolas a un proyecto dentro de un entorno distinto
al entorno 'Común'.

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

#### Filtro por Recurso de Cliente

Muestra los recursos que coinciden con las clases seleccionadas.

#### Filtro por Rol de Cliente

Muestra los recursos que coinciden con los roles seleccionados.

#### Filtro por variable

Muestra los recursos que coinciden con las variables

#### Entorno

Selecciona los entornos a mostrar o ocultar.

#### Excluir entornos seleccionados

Excluye los entornos seleccionados, mostrando los recursos de los demás entornos de Clarive.

#### Seleccionar tópicos por categorías

Selecciona las categorías que se desean mostrar. Estas categorías sólo pueden ser de tipo cambio.

#### Campo Revisión

Especifica el ID del campo revisión que pertenezca a las categorias seleccionadas (este ID debe ser igual para todos
ellos). Se necesita para visualizar datos en modo 'Revision'.

#### Condición avanzada JSON/MongoDB

Permite añadir un filtro para filtrar los topicos y/o categorías a mostrar.
