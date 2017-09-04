---
title: Proyecto
index: 5000
icon: project
---

Un *Proyecto* es el [grupo de seguridad](/concepts/scope) más común de Clarive.

En Clarive, un Proyecto es una colección de [tópicos](/concepts/topic), y se define en base a los requerimientos de cada
organización. Por ejemplo, un proyecto de Clarive puede ser:

- Un proyecto de desarrollo de software.
- Un sistema.
- Un grupo de componentes de software.
- Algo más genérico como una aplicación.

Los tópicos pueden pertenecer a uno o más proyectos (incluso a ninguno) pero no es un requisito. Por ejemplo los tópicos
de una categoría de tipo Cambio, deben de pertenecer a un único proyecto.

Los tópicos de una Categoría de tipo Release pueden pertenecer a uno o varios proyectos o no tener proyecto.

## Variables del Proyecto

Cada proyecto puede tener un conjunto de variables diferentes especificadas por cada proyecto. Incluso, por cada
[entorno](/concepts/environment), se pueden especificar diferentes valores.

Las variables se pueden configurar en una [plantilla de proyecto](/how-to/project-template) en función del entorno
o de los entornos en los que se encuentran disponibles o tienen asignadas un determinado valor. Éstas se pueden
referenciar dentro de proyectos de una forma parecida a cuando se referencian variables comunes, siendo la diferencia
que luego sus valores son importados seleccionando del combo de `Importar Configuración` aquella plantilla de entorno en
que las mismas fueron configuradas.

### Copia de variables entre Entornos

Definir variables puede ser un arduo proceso, y es muy común que para diferentes entornos quieras tener las mismas
variables pero con valores diferentes. Es por lo que Copiar variables a otro entorno puede ser de ayuda. Si las
[variables](/concepts/variable) están marcadas con el flag Copiar, se copia el valor actual.

## Variables en la naturaleza

Las variables de la naturaleza se construyen a partir de las naturalezas seleccionadas y sus reglas de tipo blueprint.
