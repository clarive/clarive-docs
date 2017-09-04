---
title: cla db - Utilidades de la base de datos
index: 5000
icon: console
---

`cla db`: Comando gestionar el esquema de la base de datos.

### db-reindex

Reindexa todas las tablas de la base de datos, aplicando y actualizando de nuevo los índices recomendados para el
producto.


`--drop` - Descarta los índices conocidos (producto) antes de reindexar.

`--collection [name]` - limitar el reindex sólo a este nombre de colección (ejemplo. `topic`, `master`, etc.)

**CUIDADO**: Un reindexado puede llevar desde unos pocos minutos hasta muchas horas, y puede bloquear el acceso a la
base de datos durante el proceso. Así que asegúrese de planificar por adelantado para el tiempo de inactividad.


### db-dump

Vuelca los datos de una selección de colecciones de la base de datos MongoDB utilizando la utilidad `mongodump`.

Las colecciones volcadas no tienen grandes *"blobs"*, solo incluye cosas como tópicos, recursos e información de
administración. El objetivo es tener una forma de crear un volcado rápido para enviar a soporte que no sea tan grande
como un volcado de base de datos completo.

Se necesita una instalación local de un cliente MongoDB para que este comando funcione, y el comando `mongodump` debe
estar en la ruta.

`--all` - Descarga todas las colecciones, en lugar de sólo las esenciales.
