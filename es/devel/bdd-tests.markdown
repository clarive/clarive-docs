---
title: BDD tests
index: 5000
icon: page
---

# Introducción

## BDD

*Behavior-Driven Development* o BDD se trata de un proceso de desarrollo de software, relacionado con el área de QA
donde se busca un lenguaje común entre la parte técnica y la de negocio de manera que a partir de ese lenguaje común, se
creen los casos de prueba (Escenarios) de un nuevo desarrollo.

Mediante este método, las pruebas de aceptación se definen utilizando historias de usuario (features):

    "Como [rol] quiero [X características] con la finalidad de [los beneficios]"

Utilizando la frase anterior, podríamos describir los criterios de aceptación para las historias de usuario mediante los
Escenarios:

    Dado [contexto inicial],
    Cuando [se produce el evento],
    Entonces [resultado esperado]

Resumiendo, el ciclo de los tests BDD es el siguiente:

- Escribir las historias de usuario.
- Escribir los posibles escenarios.
- Automatizar las pruebas de aceptación.

Con la idea de tener un mismo marco de comunicación entre desarrolladores, equipo de QA y roles de negocio o no
técnicos, lo más importante es tener un lenguaje común: Gherkin

## Gherkin

Las historias de usuario son escritas Product owners o no tan técnica como los desarrolladores. En BDD, lo que se
realiza es automatizar el testing. Aparte de tener las historias de usuario tal y como se realiza en una metódologia
SCRUM, cada historia de usuario se escribirá utilizando un lenguaje especial, Gherkin, y se guardarán en ficheros con
extensión *.feature* (dentro del directorio *ta/* generalmente).

Gherkin es un lenguaje (DSL) cercano al lenguaje natural fácil de entender por negocio y por los usuarios. La idea es
contar qué es lo que hace el software más que detallar el cómo. Se trata de un lenguaje que tan solo tiene 5 sentencias:

    Feature
    Scenario
    Given
    When
    Then

Estas features se asemejan a las historias de usuario. Y como es usual en las historias de usuario, deben tener el
*Como*, *Quiero* y *Para*. Por ejemplo, para la historia de usuario "Acceder a la herramienta":

    Feature: Tener acceso a Clarive Software para crear pases
    Como Administrador
    Quiero poder acceder a Clarive
    Para poder realizar despliegues

Como se ve en el ejemplo, Gherkin tambien nos sirve para generar documentación y para automatizar los futuros tests,
haciendolo con un lenguaje accesible a todo el mundo.

Más adelante, para ejecutar los tests, necesitaremos alguna herramienta que interprete los ficheros *.feature* (Cucumber
por ejemplo). Para ello, es necesario que alguien 'traduzca' el lenguaje natural utilizado en estos ficheros en código
que sea interpretado por el sistema.

Antes de realizar esta traducción, es necesario escribir los diferentes escenarios asociados a cada historia de usuario,
que nos de ejemplos de coomo debe comportarse el sistema con el desarrollo que se realiza en la historia.

Esos escenarios serán el paso intermedio entre la historia de usuario y la implementación de una prueba automatizada. Un
escenario describe un ejemplo de comportamiento del sistema, son condiciones de aceptación de una historia de usuario.

Un escenario está compuesto de pasos:

    Given (condición previa para el escenario),
    When (ejecutar una accion en la aplicación),
    Then (el resultado esperado)

Si seguimos con la historia de usuario anterior, un escenario seria:

    Given yo soy el administrador de Clarive
    When yo creo un pase
    Entonces desde el monitor puedo seguir el progreso del pase

Ahora es necesario definir el escenario. Por ejemplo en este escenario tipico de tests BDD:

    Scenario: Cutting vegetables
    Given a cucumber that is 30 cm long
    When I cut it in halves
    Then I have two cucumbers

Podríamos escribir, utilizando expresiones regulares, por ejemplo, la siguiente definición:

    Given qr/cucumber that is "(.*?)" cm long/, sub {
        # Aqui se escribe el Código Perl
    }

    When qr/I cut it in halves/, sub {
        # Aqui se escribe el Código Perl
    }

    Then qr/I have two Cucumbers/, sub {
        # Aqui se escribe el Código Perl
    }

# Instalación

Las features se ejecutan en un navegador Firefox mediante Selenium WebDriver.

## Selenium WebDriver

El servidor (*standalone*) está incluido dentro de la carpeta *local/* si y solo si se instala el paquete *dev* de
Clarive. Este paquete se instala mediate el comando `cla stew install clarive-dev`. Esto instala tanto el servidor como
el Webdriver necesario.

## Firefox

Es necesario que el servidor donde se van a ejecutar los tests también tenga instalado el navegador Mozilla Firefox con
interfaz gráfica. Generalmente este navegador viene por defecto instalado casi todas las distribuciones Linux y se
pueden comprobar ejecutando el comando:

    firefox -v

En caso de no tenerlo instalado podemos seguir las intrucciones indicadas [aqui <img class='ext-link'
src='/static/images/icons/window-new.svg' />](https://support.mozilla.org/en-US/kb/install-firefox-linux)

Una vez instalado comprobamos que funciona y que se abre una ventana nuevo de Firefox:

    firefox

### Error:no display specified

En caso de que aparezca este mensaje de error, necesitamos definir la variable de entorno `$DISPLAY`. Existen varias
soluciones para este problema en función del sistema operativo. Para definir la variable `$DISPLAY`, ejecute `export
$DISPLAY=:0` antes de ejecutar Firefox.

# Uso

## Ejecución de tests

Para la ejecución de los tests BDD, necesitaremos tener arrancado el servidor de Selenium:

    java -jar /opt/clarive/local/bin/selenium-server-standalone.jar

Ejemplo desde una instalación estándar de Clarive.

Además arrancar el servidor Clarive con una base de datos 'test' (es necesario crear el fichero de entorno .yml
correspondiente) y con el parámetro CLARIVE_TEST establecido a '1':

    CLARIVE_TEST=1 /opt/clarive/clarive/bin cla web-start --env test --migrate-yes

Ejemplo desde una instalación estándar de Clarive. La etiqueta 'migrate-yes' es opcional pero recomendable.

Es posible ejecutar todos los tests a la vez, ejecutar los tests que hay en una carpeta (y subcarpetas) especifica
o ejecutar un test en concreto. Para ello, hacemos uso del comando `cla proveui <tests>`

    cla proveui ta/                            // Ejecuta todos los tests BDD
    cla proveui ta/admin                       // Ejecuta todos los tests que se encuentran dentro de la carpeta Admin
    cla proveui ta/user-actions/login.feature  // Ejecuta solo los tests incluidos en esta feature

Siempre se deben ejecutar desde la ruta `/opt/clarive/clarive`.

# Estructura

## BDD tests

Todos los tests BDD se encuetran dentro de la carpeta `ta/`. Dentro de ella tenemos la siguiente estructura:

    ├── ta
        └── lib
        └── <area>
            └── <sub_area>
                ├── <fichero-feature>.feature
                ├── <fichero-feature>.feature
                ├── <fichero-feature>.feature
                └── step_definitions
                    └── basic_steps.pl

En la estructura de arriba vemos como se han dividido por carpetas cada área y subárea de la herramienta. Además, en
cada ruta donde exista un fichero `.feature` deberá existir una carpeta llamada `step_definitions`, y, a su vez dentro,
un fichero `basic_steps.pl`.

Estos ficheros `basic_steps.pl` contienen la 'intrepretación' del lenguaje. Es decir, una vez definido el escenario en
lenguaje Gherkin dentro del archivo `.feature`, `basic_steps.pl` se encargará de traducir cada línea del `.feature`en
código Perl para la ejecución del test.

Resumiendo, si tenemos utilizamos el ejemplo anterior. El archivo `ta/test.feature` seria este:

    Scenario: Cutting vegetables
        Given a cucumber that is 30 cm long
        When I cut it in halves
        Then I have two cucumbers

Mientras que el fichero `ta/step_definitions/basic_steps.pl` contiene la interpretación:

    Given qr/cucumber that is "(.*?)" cm long/, sub {
        # Aqui se escribe el Código Perl
    }

    When qr/I cut it in halves/, sub {
        # Aqui se escribe el Código Perl
    }

    Then qr/I have two Cucumbers/, sub {
        # Aqui se escribe el Código Perl
    }

### Given, When, Then (pasado, presente, futuro)

De manera resumida, se utiliza **Given** para indicar el contexto donde ocurre el escenario, **When** para indicar cómo
interactuar con el sistema y **Then** para comprobar que el resultado es el que se espera:

- Given (un contexto): El paso *Given* se utiliza para describir el contexto inicial del sistema, describe las
  condiciones previas para la prueba. Por lo general es algo que sucedió en el pasado, por lo que se suelen expresar en
  pasado, para que sea más obvio indicar estas acciones.
- When (algo ocurre): El paso *When* se utiliza para describir un evento o una acción, por ejemplo una persona que
  interactúa con el sistema, en este caso escribiremos el evento en presente.
- Then (esperas que pase algo): El propósito del paso *Then* es observar los resultados, por lo que se utiliza para
  describir los resultados o resultados esperados, por lo que escribiremos el Step en futuro.

Cuando no se tiene mucha experiencia con BDD, un fallo habitual es mezclar el When con el Then, una manera fácil de no
hacerlo es usando los tiempos verbales.

## Carpeta lib/

En ocasiones, los pasos pueden quedar largos y complejos, dificiles de leer para alguien que no los ha escrito. Por
ello, hacemos uso de librerias internas en las que definimos algunas de las funciones de cara a simplificar los
`basic_steps`. Estas librerias tambien son muy utiles si los pasos se repiten en diferentes escenarios, nos permite no
escribir código duplicado.

Dentro de la carpeta `lib/` tenemos dos tipos de archivos, los `.pm`, librerias estandar y un `login_steps.pl` donde se
encuentran todos los pasos necesarios para realiar el login en Clarive.

## Uso del login\_steps.pl

Este archivo se tiene que incluir en todos los ficheros `basic_steps.pl` que se encuentren en la carpeta `ta/`. Es el
encargado de realizar el login en Clarive. Es necesario incluirlo en todos los `basic_steps.pl` que desarrollemos
mediante el uso del `do`:

    do 'ta/lib/login_steps.pl';

### Creación y uso de librerías

La carpeta `lib/` contiene librerias creadas específicamente para los tests BDD. Dentro de los archivos `.pm`
encontramos funciones genéricas que el usuario puede utilizar en los archivos `step_definitons`. Estos ficheros estan
divididos por categorias, no obstante si en desarrollador considera necesario crear uno nuevo puede realizarlo siguiendo
la nomeclatura utilizada en los ya existentes.

Todos las librerías comienzan con la definición del nombre de la libreria:

    package TestComponentExplorer;

Que luego se utilizará en los `basic_steps.pl`. Así, dentro de estos ficheros tendremos la llamada a la libreria:

    use TestComponentExplorer;

Con ello ya podremos utilizar todas las funciones definidas en la libreria:

    TestComponentExplorer->node_in_explorer_is_visible('Deliver');

## Uso de Bases de datos

Para la ejecución de los tests, se disponen de bases de datos predefinidas, estas son algunas de ellas:

    TestPermissionsTopicFields.pm
    TestPermissionsTopic.pm
    TestPermissionsUser.pm

Estos ficheros está ubicados dentro de la ruta:

    /opt/clarive/clarive/lib/Baseliner/SetupProfile/

Ejemplo desde una instalación estándar de Clarive.

Cada una debe contener lo necesario para probar las diferentes áreas y funcionalidades de la herramienta. En caso de que
se necesite añadir algun usuario especifico o rol, se realizará en el fichero correspondiente a los tests a ejecutar.

# Diseñando Features

## Features

Para describir los escenarios de cada una de las funcionalidades de Clarive, utilizaremos el mismo lenguaje Gherkin que
se ha descrito anteriormente. De forma general, comenzaremos el fichero `.feature` describiendo, la historia de usuario:

    Feature: User change password
        As a user
        In order to maintain application security
        I want to be able to change my password.

A continuación, describimos las precondiciones de las pruebas, estas precondiciones son comunes para todas los
escenarios que describiremos a continuación:

    Background:
       Given "TestCommon" database
         And user "can_change_password" is logged in
         And user opens "change password" window

Por último escribimos el escenario con un lenguaje lo más natural posible, ya que será en el fichero `basic_steps.pl`
donde 'traduciremos' el lenguaje natural en código:

       Scenario: User can change password
         Given user fills "oldpass" with "<old_password>"
           And user fills "newpass" with "<new_password>"
           And user fills "pass-cfrm" with "<repeat_password>"
         When user confirms
         Then user can logs in as "can_change_password" with "<repeat_password>"
        Examples:
           | old_password | new_password | repeat_password |
           | password     | new_password | new_password    |

En este ejemplo vemos que es posible utilizar variables para utilizar el mismo escenario cambiando los valores, asi
ahorramos volver a escribir el escenario para cada situación.

Por norma general, escribiremos primero los casos de prueba correctos (*happy paths*) y a continuación los casos de
prueba excepcionales o que deben finalizar con errores.

### Buenas prácticas a la hora de escribir Features

#### 1. Las Feature deben probar partes o funcionalidades de la herramienta

Una Feature representa una funcionalidad del software que se quiere construir, características que piden los usuarios,
por eso se les da ese nombre. Por ejemplo, "Realizar un login" representaría una Feature.

#### 2. Usar el mismo idioma que los clientes

Gherkin es un lenguaje muy cercano al lenguaje natural que facilita la comunicación entre negocio, devs y QA.

#### 3. Organizar las Features

Una forma útil de organizar los escenarios, por ejemplo, por la funcionalidad que se prueba.

#### 4. Escribir escenarios lo más independientes posible

Lo ideal es que no haya ningún tipo de acoplamiento e independencia entre los Scenarios, que sean lo más independientes
y autónomos unos de otros.

#### 5. Evitar el uso de conjunciones en un mismo Paso

Cada paso debe hacer una cosa. Cuando hay un mismo paso que contiene dos acciones separadas mediante una *and*
probablemente tendrás que dividirlo en dos *steps* diferentes. El tener una acción en cada paso aumenta la capacidad de
reutilización. Esta no es una regla general, puede haber en un mismo Step dos acciones, sin embargo, la mayoría de las
veces es mejor evitarlos.

#### 6 Escribir una narrativa

Las narrativas describen lo que una Feature hace o de lo que trata. Las narrativas son importantes para saber qué va
a implementar (y, por lo tanto, va a ser probado) esa feature en primer lugar. También contienen una breve descripción
de la funcionlidad para que otros usuarios que la lean obtengan un conocimiento aproximado de qué se trata sin leer los
escenarios.

#### 7. Usar los Background de manera coherente

Si utilizamos los mismos *steps* en el comienzo de todos los escenarios de una Feature, lo ideal es quitar esos steps de
los escenarios y ponerlos bajo la sección de Background de la Feature. Los Background se ejecutan antes de cada
escenario. Pero hay que tener cuidado de no poner demasiados Steps en el Background pues pueden llegar a ser difíciles
de entender y de mantener.

# Diseñando los basic\_steps

A la hora de diseñar los basic steps, por norma general deben de estar ordenados en función del tipo de paso, es decir,
primero se definen los Given, posteriormente los When y por último los Then.

## Añadiendo nuestras propias clases CSS

Para realizar los tests es necesario interactuar con las diferentes clases CSS que se disponen en la herramienta. El
equipo podrá añadir las clases necesarias para identificar un elemento **siempre** siguiendo una nomeclatura donde la
clase comenzará con `ui-` y un nombre representativo del elemento en cuestión.

Todas las modificaciones de este tipo que se realicen deberán ir en un commit separado al diseño de los tests y de las
features.
