---
title: Gestor de Repositorios de Artefactos
index: 5000
icon: artifacts
---

Clarive cuenta con un gestor de repositorios de artefactos integral con capacidad para gestionar la entrega de
artefactos (o componentes) para crear herramientas como Maven o afines.

Las características clares del gestor de artefacts de Clarive son:

- repositorio servidor de toda clase de ficheros (o artefactos), que se extienden de ejecutables en binario hasta.
  bibliotecas y metadatos empaquetados.
- los ficheros publicados son accesibles a través de navegación HTTP(S).
- un navegador integral a la herramienta con búsqueda y etiquetado.
- repositorio remoto proxy.
- artefacto de base de datos indizando un almacenamiento.
- control de acceso a artefactos y directorios.
- grupos de repositorios.

El sistema Clarive de gestión de repositorios de artefactos se maneja por una serie de tres recursos:

- Repositorio de Artefactos Local (ArtifactLocal).
- Repositorio de Artefactos Remoto (ArtifactRemote).
- Grupo de Repositorios (ArtifactGroup).

La gestión de repositorios en Clarive es sencilla, a la diferencia de otras harramientas del mercado. Un repositorio
local apunta a una ubicación en el sistema de ficheros (o en la base de datos) que contiene una estructura de
artefactos. Un repositorio remoto apunta a un URL que puede suministrar un determinado artefacto. Un grupo es una serie
ordenada de artefactos tanto locales como remotos.

Para crear su primer repositorio, se empieza creando un recurso de clase __Repositorio de Artefactos Local__. Léase
abajo para más información.

## URL Root

Todos los repositorios servidos por Clarive parten del url base `/artifacts/repo`:

    http(s)://[clarive-server:port]/artifacts/repo/[url-prefix]

## Repositorio de Artefactos Local (ArtifactLocal)

Un repositorio de artefactos localde Clarive es una ubicación de directorios donde se almacenan artefactos y donde los
mismos se hacen accesibles a través de una ruta URL.

El recurso ArtifactLocal representa una ubicación en el sistema de ficheros que contiene una estructura de directorio de
artefactos con un prefijo URL correspondiente.

Por ejemplo, para un recurso tipo Repositorio Local denominado "MyRepo" puede que le haga falta definir un directorio
local pra almacenar ficheros en la siguiente ubicación:

    /opt/repositories/myrepo

y un prefijo URL:

    myrepo

La base URL para este repositorio sería:

    http(s)://[clarive-server:port]/artifacts/repo/myrepo

### Crear un recurso de Repositorio de Artefactos Local

El requisito mínimo para la creación de un repositorio local es el establecimiento de un `Nombre` de recurso, la
definición de un `Prefijo URL` y una `Ruta Local al Repositorio`.

- **Nombre** - el nombre no influye ninguna de las operaciones asociadas con el URL o con el directorio.
- **Prefijo URL** - ésta es la parte de la ruta URL después de `/artifacts/repo` donde estarán accesibles los
  repositorios y sus ficheros a los usuarios, a los scripts y los sistemas de configuración que dependen de ella.
- **Ruta Local al Repositorio** - la ubicación física del repositorio de artefactos en el repositorio del sistema de
  ficheros del servidor, también denominada una _ruta root_. En el caso de no existir la ruta local, Clarive la creará.

#### Selección Automática de Ruta Local

En el caso de no haberse definida ninguna ruta local a la hora de guardar el recurso, Clarive establecerá la ruta a una
combinación de la variable de configuración global `config.artifacts.path` y del prefijo URL.

Después de guardar, vuelva a cargar el recurso para ver el nuevo valor.

#### Modo de Acceso: Público

Los repositorios locales con el modo de acceso **Público** pueden ser navegados a través de la interfaz, y los
artefactos que contiene pueden ser descargados por cualquier usuario que tenga acceso al URL.

#### Modo de Acceso: Oculto

Los repositorios locales son públicos por defecto. En modo **cerrado** sin embargo, nadie puede acceder los
repositorios a no ser que sea mediante un grupo de repositorios.

Por eso el modo cerrado es ideal para definir ubicaciones de almacenaje locales que se podrán combinar posteriormente
a conformar un grupo de repositorios.

### Modo de Coincidencias Exactas

Por defecto se encuentran los ficheros de repositorio locales por coincidencia exacta con el nombre de fichero
solicitado.

Para buscar coincidencias parciales, use el modo **Prefijo**.

### Modo de Coincidencias de Prefijo, Listas blanca y negra

En el modo de coincidencias **Prefijo**, no hace falta que los ficheros servidos por un directorio local coincidan
exactamente. Clarive procurará equiparar todos los posibles ficheros que **comiencen** con el nombre de fichero
solicitado. Un repositorio de artefactos local puede contener artefactos de lista blanca o negra, así permitiendo que
los administradores controlen de manera más eficaz las clases de ficheros devueltas por Clarive.

Para una mayor comprensión de como funcionan las listas blancas y negras, ante todo hace falta que distingamos entre las
dos clases de listado de datos introducidos:

- ficheros - un nombre de ficheros solicitado por el usuario, la herramienta de configuración etc.
- imágenes - un fichero localizado por Clarive dentro del sistema de ficheros.

En el caso de que se devuelve más de una imagen correspondiente a una determinada solicitud de fichero, se devolverá la
primera coincidencia.

Ejemplo:

    Fichero solicitado:

    http://clarive/artifacts/repo/myrepo/file.jar

    Imágenes que coinciden:

    http://clarive/artifacts/repo/myrepo/file_v01.jar
    http://clarive/artifacts/repo/myrepo/file_v00.jar

    Fichero servido:

    http://clarive/artifacts/repo/myrepo/file_v01.jar

#### Expresión regular

Todos los listados son expresiones regulares, por lo tanto hace falta introducirlos con el siguiente separador `|`
(barra vertical).

#### Ficheros de lista blanca

Se trata de un listado de patrones de fichero que puede solicitar el usuario o la herramienta de configuración. Los
patrones pueden coincidir con cualquier parte del nombre de fichero o del URL solicitado.

Una lista blanca vacía significa que se puede solicitar CUALQUIER patrón de fichero. En el caso de que el fichero no
coincide con el patrón, se descarta el fichero de forma inmediata.

#### Ficheros de lista negra

Un listado de todos aquellos **sufijos** que no pueden ser solicitados ni por el usuario ni por la herramienta de
configuración.

Una lista negra vacía significa que NINGUNO se encuentra en la lista negra.

**Nótese**: aunque un fichero esté en la lista negra, puede ser servido de  todas formas gracias a una lista blanca tipo
imagen. Véase abajo.

Ejemplo:

    Fichero solicitado:

    http://clarive/artifacts/repo/myrepo/file.jar

    Ficheros en la lista negra:

    -source|-sources

    Imágenes que coinciden:

    http://clarive/artifacts/repo/myrepo/file.jar
    http://clarive/artifacts/repo/myrepo/file-sources.jar

    Fichero servido, el cual excluye los ficheros en la lista negra:

    http://clarive/artifacts/repo/myrepo/file.jar

#### Imágenes en la lista blanca

Las imágenes son ficheros que se encuentran en el repositorio de artefactos y que coinciden con el nombre de fichero
detectado.

El patrón de imagen de lista blanca coincidirá con cualquier parte de la ruta o del nombre de fichero solicitados.

**Importante**: por más que un fichero se encuentre en una lista negra, si existen imágenes de lista blanca que
coincidan, serán devueltas las mismas por Clarive al solicitante. Eso sí, se devolverán únicamente imágenes de la lista
blanca que tengan el nombre de fichero solicitado.

#### Imágenes de lista negra

Las imágenes son ficheros que se encuentran en el repositorio de artefactos y que coinciden con el nombre de fichero
detectado.

## Repositorio de Artefactos Remoto (ArtifactRemote)

Un repositorio de artefactos remoto se trata de una ubicación URL desde donde Clarive puede descargar artefacts y servir
los mismos al usuario.

Los repositorios de artefactos remotos permiten que Clarive actúe como proxy entre el usuario y el artefacto remoto.

### Crear un Repositorio de Artefactos Remoto

Para crear un repositorio de artefactos remoto sólo hace falta utilizar los campos de recurso `Nombre` y `URL del
repositorio remoto`.

- **Nombre** - el nombre representa simplemente el nombre del recurso y no repercute en cómo se utiliza el repositorio
  ni tampoco cómo éste se accede de forma remota.
- **URL del repositorio remoto** - se trata de un URL de un repositorio de artefactos capaz de entregar los ficheros
  solicitados. Este URL se sirve típicamente mediante Internet, si bien puede apuntar a otros repositorios dentro de una
Intranet o la nube privada de una sociedad.

#### Asociación Remota a Local

Para poder habilitar un repositorio remoto para ser utilizado, primero hay que disponer de un repositorio local que
sirva de puente al remoto.

El establecimiento de una asociación de repositorios local-remota crea una copia guardada en caché del repositorio
remoto. De esta manera, se guardarán en caché local (en un directorio de servidor) los ficheros a ser solicitados
a menudo por las configuraciones, y los mismos podrán ser indizados, buscados y navegados por los usuarios.

## Grupo de Repositorios (ArtifactGroup)

Un grupo de repositorios se trata de una conjunto **ordenado** de repositorios locales que han sido agupados de manera
lógica en un prefijo URL.

¿Para que utilizar grupos de repositorios?

1. para disponer de repositorios locales organizados de diferentes maneras y en una variedad de ubicaciones, sin que
ello repercuta en usuarios ni en configuraciones, que se pueden ver impactados a la hora de reorganizar un prefijo URL.
2. para disponer de una serie de repositorios de **contingencia**, así permitiendo al usuario o sistema de configuración
ir probando varias ubicaciones antes de que se devuelva un código 404 (no encontrado).

Es precisamente por estos motivos que recomendamos el uso de grupos de repositorios. Los grupos suponen para los
usuarios un punto de entrada único a la jerarquía del repositorio de artefactos.

### Mapeo del URL de grupo a local

Serán sustituidos los prefijos de URL de repositorios locales por el prefijo grupal a la hora de acceder un repositorio
local a través de un grupo.

Supongamos por ejemplo que disponemos del siguiente repositorio:

    url_prefix: mylocal

y que solemos poder acceder el siguiente fichero dentro del repositorio local:

    http://clariveserver/artifacts/repo/mylocal/dir1/file1.jar

y que lo siguiente se trata de un prefijo grupal que corresponde a un grupo que contiene el mencionado repositorio
local:

    url_prefix: mygroup

Entonces el siguiente URL será puesto a la disposición de los usuarios:

    http://clariveserver/artifacts/repo/mygroup/dir1/file1.jar

lo cual tiene el efecto de sustituir la parte de la ruta URL `mylocal/` anterior con la nueva.

## Mensajes de Error de Repositorio

Los repositorios podrán generar los siguientes errores y mensajes de error:

#### 400 Bad Request

Este mensaje de error significa que el prefijo del repositorio no existe en el sistema de gestión de repositorios de
Clarive.

A continuación de expone un ejemplo en Maven:

    [ERROR] Plugin org.apache.maven.plugins:maven-clean-plugin:2.5 or one of its
    dependencies could not be resolved: Failed to read artifact descriptor for
    org.apache.maven.plugins:maven-clean-plugin:jar:2.5: Could not transfer
    artifact org.apache.maven.plugins:maven-clean-plugin:pom:2.5 from/to central
    (http://clarive:8080/artifacts/repo/local): Failed to transfer file:
    http://clarive:8080/artifacts/repo/local/org/apache/maven/plugins/maven-clean-plugin/2.5/maven-clean-plugin-2.5.pom.
    Return code is: 400, ReasonPhrase:Bad Request. -> [Help 1]

Revise su prefijo URL, la parte del mismo que sigue directamente la parte`/artifacts/repo/`.

#### 404 File Not Found

Este error denota que un artefacto no se ha encontrado en el repositorio, pero que el respositorio sí que existe.

En Maven el error podrá tener el siguiente aspecto. Nótese que aquí no se ve el código del error:

    [ERROR] Failed to execute goal on project my-app: Could not resolve
    dependencies for project com.mycompany.app:my-app:jar:1: Failed to collect
    dependencies at com.dbcx.core:dropbox-core-sdk:jar:LATEST: Failed to read
    artifact descriptor for com.dbcx.core:dropbox-core-sdk:jar:LATEST: Failed
    to resolve version for com.dbcx.core:dropbox-core-sdk:jar:LATEST: Could
    not find metadata com.dbcx.core:dropbox-core-sdk/maven-metadata.xml in
    local (/opt/mavenprj/.m2/repository) -> [Help 1]

El error 404 se puede deber a una configuración equivocada en el script del usuario o de configuración/empaquetación del
proceso, o a una decisión de parte de la sociedad a no poner a la disposición del usuario a través de una lista negra.

# Uso del Repositorio de Artefactos de Clarive con Gestores de Paquetes

El sistema Clarive de gestión de repositorios de artefactos se puede utilizar en combinación con un amplio abanico de
sistemas de gestión de paquetes diferentes, y no sólo con sistemas de configuración como Maven.

El uso de repositorios privados supone un método ideal para la publicación y el control de las versiones de los paquetes
utilizados dentro de una sociedad.

A continuación se exponen algunos ejemplos del uso de Clarive en combinación con una variedad de gestores de paquete
populares.

### Node NPM

El gestor de paquetes de NodeJS NPM recurre al concepto de `registro`, siendo éste un URL que contiene un repositorio de
NPM.

Para conseguir que Clarive represente como proxy un registro de NPM, primero hay que crear un remoto que apunta a un
registro de Nodo público, como (el registro oficial de Nodo público):

    Remote URL: https://registry.npmjs.org/

Luego hay que crear un repositorio local para guardar en caché los artefactos descargados y conectar el mismo al remoto.

Una vez que se hayan creado los recursos de Clarive, puede proceder a setear el registro npm registry mediante la línea
de comando. En el supuesto de que setea el prefijo URL `local-npm`, podrá instalar paquetes de Node JS a través de
Clarive:

    npm install --registry http://clarive:8080/artifacts/repo/local-npm babel

o simplemente configure el registro dentro de su fichero `$HOME/.npmrc` que apunta al repositorio NPM de Clarive que
acaba de crear:

    ; apuntar el repositorio NPM local en Clarive
    registry = http://clarive:8080/artifacts/repo/local-npm

### Python PyPI

El sistema de gestión de paquetes Python PyPI puede utilizar Clarive para representar como proxy y controlar los
paquetes que se han descargado.

Primero hay que crear un recurso de artefacto remoto que apunta al URL remoto de un repositorio de Python PyPI:

    URL remoto: http://pypi.python.org/simple/

antes de proceder a crear un repositorio local para guardar en caché los artefactos descargados y conectar el mismo al
remoto.

Ahora sólo falta setear el URL de url-prefix del gestor de artefactos de Clarive artifact manager url-prefix mediante
`--index-url` (o `-i`) de `easy_install` de Python.

    easy_install -i http://clarive:8080/artifacts/repo/pypi/ [nombre_del_paquete]

### Perl y CPAN

El uso de Clarive en combinación con los gestores de paquete de CPAN es sencillo. Simplemente cree un remoto que apunta
a uno de los muchos mirrors  CPAN mirrors existentes en Internet. Por ejemplo:

    URL remoto: https://cpan.metacpan.org

y cree el recurso local con un prefijo URL `cpan`, añadiendo el recurso remoto al campo Repositorios Remotos.

Ya puede proceder a la instalación de los paquetes de Perl mediante representación proxy a través de Clarive.

    cpanm --mirror-only --mirror http://clarive/artifacts/repo/cpan Mooses
