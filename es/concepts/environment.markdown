---
title: Entornos
index: 5000
icon: ci-bl
---

En DevOps, un entorno se define típicamente como un lugar donde se despliegan los cambios. Pero más que eso, podemos
decir que un entorno es un grupo lógico de Recursos.

### Entorno como Recurso

En Clarive, un entorno por si mismo es un **Recurso**. Crea un nuevo Recurso y estarás creando un nuevo entorno.

### ¿Como puedo configurar el contenido de un entorno?

Se puede hacer principalmente de dos formas:

- Para cada Recurso que creemos podemos definir a que entorno pertenece.  Algunos Recursos no soportan esto como los
  Recursos de clase Proyecto, pero otros sí como servidores o estados.
- Para cada [alcance](/concepts/scope) o [proyecto](/concepts/project), podemos definir que Recursos pertenecen a un
  entorno dado para ese alcance en particular.

### Nombrado de entornos

*DEV, TEST, QA, PRE, PREP* (preproducción), *PRO* y *PROD* (producción) son todos los nombres que se usan habitualmente.
Por convención, proponemos que el nombre de los entornos esté limitado ente dos y cuatro letras.

### El Entono Común (*)

El *entorno común* es un entorno especial en Clarive que ampara los Recursos y las [variables](/concepts/variable) que
son comunes para todos los entornos o que no tienen entorno especificado.

Por ejemplo, en los siguientes Recursos:

- Una clase de Recurso GenericServer estará disponible para todos los entornos o solo para algunos. Aquí el entono común
  significa **todos**.
- En una clase de Recurso GitRepository se asignará el entorno común, pero significa **NINGUNO**, ya que un repositorio
  de código fuente no tiene el concepto de entorno por sí mismo (por ejemplo, no creas un repositorio de Git para cada
entorno).

### Heredados: Baseline y bl

Las antiguas versiones de Clarive tienen el concepto de *bl*, que se traduce como línea base, pero actualmente eso
significa entorno.

Internamente, entorno es almacenado con el nombre `bl`, y por lo tanto es visible así en [YAML](/concepts/yaml) y otros
sitios.
