---
title: Personalizar la Interfaz de Usuario
index: 5000
icon: page
---

Algunas de las caracteristicas de la intefaz web de la aplicación de Clarive pueden ser personalizadas por el usuario
por medio del fichero `[env].yml`.

Hay dos personalizaciones básicas disponibles:

- **Ficheros de Logo** - Esta opción hace referencia al logo que se muestra en la parte superior izquierda de la
  pantalla.
- **Ficheros CSS** - Permite al usuario cargar sus propias hojas de estilo.

### Ubicación del fichero en el servidor

Desde Clarive recomendamos que estos ficheros (logos o hojas CSS) se ubiquen dentro de una carpeta `/public/` en caso
que sea un plugin o en la carpeta `/root/` en caso de feature dentro del nodo donde se encuentra el servidor web de
Clarive.

En general, el navegador va a intentar cargar el fichero desde una URL, por lo tanto los ficheros personalizados pueden
encontrarse bajo la dirección URL principal de Clarive.

Por ejemplo, si el fichero del logo se encuentra fisicamente en la rulta
`CLARIVE_BASE/features/myfeature/root/milogo.png`, entonces deberia cargar el fichero a través de la URL:

    http://miservidorclarive/milogo.png

### Cambiar el fichero de logotipo

Para cambiar los ficheros del logo de la aplicación, existen cuatro parámetros disponibles:

    logo_file: /ruta/al/logo.png
    logo_width: 150
    logo_narrow_file: /rula/al/mini-logo.png
    logo_narrow_width: 30
    login_logo: /ruta/al/login-logo.png
    login_logo_width: 180

El logo se mostrará como fuente con la etiqueta `img` en la aplicación.

El ancho es opcional, pero permite redimensionar un logo sin necesidad de editar la imagen (lo cual requiere
herramientas adicionales).

- `logo_file` - Es el logo que se muestra en la parte superior izquierda del menú principal de navegación de la
  aplicación.
- `logo_width` - Es el ancho opcional del logo que aplica al `logo_file`.
- `logo_narrow_file` - Es el logo mostrado en la parte superior izquierda del menú de navegación de la aplicación
  principal cuando está en modo estrecho.
- `logo_narrow_width` - Es el ancho opcional del logo que aplica al `logo_narrow_file`.
- `login_logo` - Es el logo que se muestra en la pantalla de login aplicación.
- `login_logo_width` - Es el ancho opcional del logo que aplica al `login_logo`

### Añadir texto a la derecha del logo

Se trata de una estrategia perfecta para identificar su instancia de Clarive en caso de que tenga más de una instancia
instalada. O simplemente para personalizar la información de la instancia.

Añada el siguiente parámetro al fichero `[env].yml`:

    logo_text: MI INSTANCIA

Reinicie y refresque la instancia. El texto se mostrará al lado del logo que se muestra en la parte izquierda, en el menú
de navegación.

### CSS personalizados

El CSS personalizado es una forma estandarizada y muy potente de agregar estilos personalizados al HTML de la aplicación
Clarive.

Para añadir sus propios estilos a la aplicación Clarive, añada el siguiente parámetro al fichero de configuración
`[env].yml`:

    custom_css: /ruta/al/miestilo.css
