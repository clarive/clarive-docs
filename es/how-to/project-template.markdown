---
title: Crear Plantilla de Proyecto
index: 5000
icon: ci-project-template
---

Cada proyecto puede contener una serie [variables](/concepts/variable) con valores establecidos específicamente para el proyecto en cuestión,
y además para cada [entorno](/concepts/environment). Cada uno de éstos puede contener valores como cadenas, números,
listados, almohadillas (diccionarios) y recursos (p.ej. naturalezas y blueprints).

Establecerlas puede convertirse en un proceso laborioso, y ocurre a menudo que distintos entornos pueden contener las
mismas variables, eso sí con distintos valores. Se puede agilizar la configuración de un proyecto agrupando sus
variables en una *plantilla de proyecto*, en la cual se establece también aquél al que están disponibles. Se referencian
aquéllas de una plantilla de proyecto en proyectos de una manera parecida a cuando se referencian de forma directa.

## Crear Plantilla de Proyecto

Seleccionar ![](/static/images/icons/ci-project-template.svg) ProjectTemplate en la barra de menús Recursos/Todos. Luego
seleccionar el botón ![](/static/images/icons/add.svg) Crear.

Introducir un nombre en el combo de `Nombre`, luego seleccionar del combo `Variables` las predefinidas que desea incluir
en la plantilla de proyecto. Seleccionar en el combo de `Entorno` el entorno en que se desea que se disponga de las
variables en cuestón. Éstas aparecerán en el orden en que se han seleccionado (en el mismo formato en que se han creado,
p.ej. valor, textarea, combo etc.) debajo del combo de `Copiar Variables A...`. De seleccionarse otro entorno en `Copiar
Variables A...`, se cambiará el actual a aquél al que se copiarán las variables.

Haga clic en `Guardar` antes de cambiar de entorno en el combo respectivo. A la hora de cambiar de uno a otro, ya no se
enumerarán las variables creadas desde el anterior debajo del combo `Copiar Variables A...`. Repita los pasos anteriores
para cuántos entornos necesite seleccionar variables.

### Copiar Variables

En el caso de necesitar el mismo conjunto de variables (u otro parecido) para más de un entorno, puede que resulte más
fácil copiar las mismas de uno a otro una vez establecido el conjunto en un determinado entorno.

Para ello, seleccionar el entorno de destino del combo de `Copiar Variables A...`. Se cambiará de forma automática el
actual aquél al que se acaban de copiar las variables. Nótese que las variables contendrán los mismos valores que en él
de su creación. Se pueden cambiar los mismos aquí. En el caso de las de tipo combo, puede seleccionar alguna de las
otras opciones disponibles en el entorno anterior.

Se puede borrar del conjunto todas las que no hagan falta.

Haga clic en `Guardar`.
