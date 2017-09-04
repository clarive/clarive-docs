---
title: cla migra - Migraciones
index: 5000
icon: console
---

`cla migra`: Ejecuta las migraciones de bases de datos, necesarias para evitar incompatibilidades entre la versión de la
base de datos y la versión de Clarive tras actualizar o instalar parches.

## Parámetros comunes

    --dry-run no realiza ninguna acción solo imprime por pantalla lo que va a hacer
    --init asegúrese de que las migraciones se inicialicen
    --yes contesta que sí a todas las preguntas
    --quiet modo silencioso
    --force no ejecuta las comprobaciones de seguridad

    --core solo ejecuta las migraciones del core
    --features solo ejecuta las migraciones de las features
    --feature ejecuta las migraciones de la feature especificada
    --plugins solo ejecuta las migraciones de los plugins
    --plugin ejecuta las migraciones del plugin especificadp

## Subcomandos

### migra-state (defecto)

Imprime el estado actual de la base de datos.

### migra-init

Inicializa la migración

### migra-start

Actualiza o desactualiza las migraciones. Las opciones son:

    --init Inicia la ejecución antes de migrar
    --path Indica la ruta de las migraciones en caso de no usar la de defecto

### migra-downgrade

Revierte una versión específica. Las opciones son:

    --version la versión que se revierte
    --path ruta a las migraciones, en vez de por defecto

#### migra-set

Establece manualmente la versión más reciente de las migraciones.

    --version <La versión que se quiere establecer>

#### migra-fix

Elimina el error de la última migración. Use *SOLO* cuando el problema esté completamente arreglado.

### migra-oneshot

Realiza la actualización o desinstalación de manera manual pasando los siguientes parámetros (por defecto actualiza):

    --version version de la migración
    --downgrade ejecuta la desinstalación
