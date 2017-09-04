---
title: Instantáneas
index: 5000
icon: slot
---

Una copia instantánea de volumen o *snapshot* es una instantánea del estado de Clarive en un momento determinado. Para
realizar está copia hay que acceder a través del menú Admin - ![](/static/images/icons/slot.svg) Instantáneas.

Para crear una instantánea, basta con pulsar en ![](/static/images/icons/add.svg) Tomar instantánea y escoger un título
y los componentes que se quieren almacenar.

Una vez seleccionados, el sistema creará la instantánea que aparecerá en la tabla con el tamaño que ocupa la
instantánea.

Esta instantánea se puede eliminar haciendo click en ![](/static/images/icons/delete.svg) o exportar
![](/static/images/icons/export.svg). Exportando la fila o filas, se descarga al servidor un fichero comprimido en
formato *.zip* con los ficheros *yml* de los componentes exportados.

Es posible importar una instantánea realizada previamente (incluso en otro sistema) mediante el servicio
![](/static/images/icons/import.svg) Importar. Clarive facilita la importación y ofrece la usuario la posiblidad de
importar todos los componentes o solo alguno de ellos.

También es posible crear instántaneas a través de las reglas utilizando el [servicio *Tomar instantánea del
sistema*](rules/palette/services/snapshot).
