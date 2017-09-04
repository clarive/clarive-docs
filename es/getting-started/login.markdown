---
title: Login
index: 4000
icon: user
---

Antes de poder acceder a Clarive, el [Administrador](/admin/user) debe de registrar al usuario. El administrador tiene
que suministrar al usuario la siguiente información:

- **Usuario** - El usuario creado dentro de la herramienta y con el que tendrá acceso a Clarive. Este usuario no es
  sensible a mayúsculas/minúsculas.
- **Contraseña** - Contraseña generada por el administrador. Sensible a mayúsculas/minúsculas.

El usuario podrá modificar la contraseña desde las preferencias de usuario, activando para ello el menú de usuario en la
parte arriba derecha de la interfaz y seleccionando *Cambiar contraseña*.

**Nota**: Por lo general, los administradores deshabilitan los privilegios de poder cambiar la contraseña cuando se
trata de un inicio único de sesión o la [autenticación LDAP/SAML](/admin/ldap) está habilitada.

### Login externo

Si se quiere realizar el login a Clarive directamente desde otra ubicación (portal web de su empresa por ejemplo), se
puede utilizar este código HTML como plantilla para crear el formulario de acceso:

```html
<textarea style="height: 250px; width: 90%">
    <form action="https://clariveserver:port/login" method="POST">
        <table border="0" cellspacing="5" cellpadding="5">
            <tr>
                <td>User Name:</td>
                <td>
                    <input type="text" name="username" />
                </td>
            </tr>
            <tr>
                <td>Password:</td>
                <td>
                    <input type="password" name="password" />
                </td>
            </tr>
            <tr>
                <td colspan="2">
                    <input type="submit" />
                </td>
            </tr>
        </table>
    </form>
</textarea>
```
