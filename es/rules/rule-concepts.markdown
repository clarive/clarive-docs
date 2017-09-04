---
title: Conceptos de regla
index: 100
icon: rule
---

Una vez que las diferentes necesidades se registran y se gestionan a través de los distintos estados que componen su
ciclo de vida, estos deben de ser desplegados y entregados como operación final del ciclo.

La gestión de reglas permite automatizar el despligue entre sistemas.

La automatización se realiza a través de ejecuciones de reglas; estas son creadas utilizando la definición de los
procesos de Clarive, la cual además, suministra todas las herramientas necesarias para su gestión.

### Tipos de reglas

Existen siete tipos de reglas, reglas de eventos, jobs, *blueprints*, informes, independientes, dashboards
y formularios.

**Eventos** - Lanzadores desencadenantes basados en acciones realizadas por el sistema. Hay tres tipos de reglas de
evento:

1. **Pre online** - Carga la regla antes de la ejecución del evento.
2. **Post online** - La regla se carga de manera síncrona con el evento.
3. **Post offline** - La regla se ejecuta tras producirse el evento.

**Cadena de pase** - Referentes a las cadenas de pase, para desplegar o realizar [rollback](/concepts/rollback).Tres
posibles pasos finales:

- *Promote* -  Despliega a otro entorno, conceptualmente otro superior, por ejemplo de pre-producción a producción.
- *Static* - Despliega al mismo entorno.
- *Demote* - Degrada a un entorno inferior, por ejemplo, de producción a pre-producción.

**Ámbito**: Cuando la regla es un evento de tipo tópico, el usuario puede asignar filtros a la ejecución de la regla.
Los tres posibles filtros son:

- *Proyectos* - Seleccionamos los proyectos con los que queremos lanzar la regla. Si no se especifícan proyectos, el
  ámbito usará todos los proyectos.
- *Categorías* - Seleccionamos las categorías con las que queremos lanzar la regla. Si no se especifícan categorías, el
  ámbito usará todas las categorías.
- *Estados* - Seleccionamos los estados con los que queremos lanzar la regla. Si no se especifícan estados, el ámbito
  usará todos los estados.

Cuando el evento es de tipo topic.modify_field, la regla solo se ejecutará en el modo pre-online.

### Pasos de un job

Cuando se crea una regla de tipo cadena de pase, se muestran cinco pasos:

- **CHECK** - Comprueba antes de crear el job, el objeto del job no está disponible todavía.
- **INIT** - Comprueba después de la creación, pero el job no se ejecuta aún.
- **PRE** - Inmediatamente después de la implementación antes de la hora programada
- **RUN** - Se ejecuta a la hora programada.
- **POST** - Fase que siempre se ejecuta cuando el trabajo ha terminado independientemente de su resultado.

### Tipos de tareas

La regla se puede dividir en siete tipos de tareas:

1. **Control** - Proporciona a la regla flujos de control, como son condicionales IF o iteraciones FOR así como tareas
   *ad-hoc*.
2. **Servicios** - Para definir el pase, puede ser:
   - *Servicios del job* - Tareas asociadas al job.
   - *Servicios generales* - De tipo general.
3. **Flujo de trabajo** - Todos los servicios relacionados con crear flujos de trabajo a través de las reglas.
4. **Blueprint** - Todas las variables (creadas como [Recurso](/concepts/variable))que pueden ser utilizadas en las
   reglas de tipo Blueprint.
5. **Reglas** - Permite incluir reglas dentro de otras reglas para simplicar el flujo. Este tipo de reglas tiene que ser
   de tipo independiente.
6. **Dashlets** - Componentes que sirven para construir los [dashboards](/concepts/dashboards).
7. **Fieldlets** - Elementos que dan forma a los formularios de los [tópicos](/concepts/topic)

### Otras reglas

- **Report** - Crea un informe con código PERL. Para más información, puede ver un *how-to* llamado [Crear un
  informe](/how-to/create-reports).
- **Servicio web** - Permite integrar servicios web en reglas.
- **Workflow** - Permite crear transiciones entre estados a través de una regla. Para que la regla sea efectiva, es
  necesario especificarla en la configuración de la categoria.
- **Independiente** - Pequeñas reglas que pueden ser utilizadas en otras reglas más complejas simplificando el sistema.
- **Dashboard** - Regla que permite al usuario crear dashboards personalizados con componentes dashlets.
- **Form** - Regla compuesta por fieldlets para crear los formularios que se usarán en los tópicos.
- **Blueprint** - Regla compuesta por variables que contruye las variables del proyecto una vez la regla es asignada
  a una naturaleza.

### Stash

El [stash](/concepts/stash) de las reglas en el sistema de Clarive mantienen el estado de los pases entre ejecuciones.
Las variables stash son utilizadas para comunicar diferentes tareas.
