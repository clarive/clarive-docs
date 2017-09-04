---
title: cla passwd - Encriptación contraseñas
index: 5000
icon: console
---

`cla passwd`: Herramienta de conversión para encriptar contraseñas.

Los subcomandos disponibles se pueden visualizar con la ayuda:

    >cla help passwd

    USO: cla [-h] [-v] [--config file] comando <comando-args>

    cla help <comando> para obtener todos los subcomandos.
    cla <comando> -h para las opciones del comando.


`cla passwd`:

- *-u <\nombre_usuario>* - Nombre de usuario al que se le encriptará la contraseña. Se trata de un parámetro obligatorio
  y puede ser definido como parámetro de entrada
- *-p <\contraseña>* - La contraseña del usuario.
- Escrita desde el teclado cuando el comando lo pida.

El cifrado se realiza mediante el parámetro *decrypt_key* o *dec_key* del archivo de configuración.
