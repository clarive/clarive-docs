---
title: Variable
index: 5000
icon: ci-variable
---

Una *Variable* en Clarive se define de manera global usando la clase de [Recurso](/concepts/resource) Variable.

Cada variable puede contener valores como cadenas de texto, número, listas, hashes (diccionarios) y Recursos.

Las variables pueden ser referenciadas en las [reglas](/concepts/rule) usando la notación `${nombre-variable}`.

Cuando se ejecuta una regla, su [stash](/concepts/stash) se carga con los valores por defecto de las variables globales.
Entonces, al continuar con la ejecución, cada valor de las variables cambia o se introducen nuevas variables en el
stash.

## Variables Obligatorias

Cada variable puede ser marcada como obligatoria. Esto afecta a las variables de proyecto (ver
[Proyecto](/concepts/project) para más información).

## Blueprint Variables

Las variables Blueprint contienen otras variables configuradas dentro de una regla Blueprint. Para poder hacer este
conjunto accesible fuera de la Blueprint (p.ej. a [plantillas de proyecto](/how-to/project-template)), ante todo hace
falta que creemos una nueva variable, definiéndose su `Tipo` como 'CI', y su `Rol de CI` y `CI Class` como 'Nature' en
los combos respectivos. Finalmente debemos crear una naturaleza como contenedor para la Blueprint seleccionada.

## Copiar variables

Cuando copias variables entre entornos (ver [Proyecto](/concepts/project) para más información), si está marcada con el
flag copiar hace que el valor sea copiado también.

## Variables de Proyecto

En cada [proyecto](/concepts/project) can have a set puede haber una serie de variables cuyos valores han sido
establecidos concretamente para ese proyecto. Es más, se pueden establecer diferentes valores para cada
[entorno](/concepts/environment).

Las variables se pueden configurar en una [plantilla de proyecto](/how-to/project-template) en función del entorno o de
los entornos en los que se encuentran disponibles o tienen asignadas un determinado valor.
