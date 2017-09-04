---
title: Análisis de Calidad de Regla
index: 5000
icon: rule
---

Un Análisis de Calidad de Regla permite asegurar que cada regla se adhiere a la buena praxis. La buena praxis se agrupa
por Normas, y cada una se ellas se puede activar/desactivar por separado. Algunas normas cuentan con una configuración
avanzada.

# Quality Gate

Se puede establecer un umbral de calidad para proteger las reglas y evitar que puedan ser guardadas en caso de que no
pase el análisis de calidad en caso de que éste informe de errores importantes de acuerdo con el nivel establecido


# Políticas

Actualmente existen seis normas básicas clasificadas con cinco tipo de severidad. Las normas que están disponibles
actualmente:

- **UnknownVariable** - informa sobre el uso de variables inexistentes o no registradas. Severidad: 5.
- **NotUsedVariable** - informa sobre variables declaradas que no están en uso. Severidad: 2.
- **Complexity** - informa sobre reglas y operaciones complejas. Severidad: 3.
- **Deprecated** - informa sobre operaciones depreciadas. Severidad: 4.
- **Rollback** - informa sobre la falta de lógica rollback. Severidad: 5.
- **Miscellaneous** - informa sobre el uso del nombre por defecto de la operación de la paleta. Severidad: 1.


# Configuración

Existen varias variables de configuración que permiten la configuración del análisis:

- `config.rules.critic.max_severity`: se podrá guardar una regla si la servidad de todas las normas incumplidas es
  inferior a la indicada.
- `config.rules.critic.policies`: políticas a analizar. Por defecto todas.
- `config.rules.critic.policies`: políticas a analizar. Por defecto todas.

Las propias políticas pueden ser configuradas. Para **Complexity**:

- `config.rules.critic.policy.Complexity.max_code_lines`: número máximo de líneas de código permitidas
- `config.rules.critic.policy.Complexity.max_nesting_level`: número máximo de líneas dentro de un Server Code
- `config.rules.critic.policy.Complexity.max_operations_count`: número máximo de operaciones por regla.
