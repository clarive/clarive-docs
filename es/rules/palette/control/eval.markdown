---
title: EVAL
index: 5000
icon: statement-perl-eval
---

Ejecuta código PERL e identifica los errores durante la ejecución almacenando el valor de retorno en la variable
*data_key* del [stash](/concepts/stash) si ésta ha sido definida.

En caso de error, la regla se detendrá y se mostrará un mensaje con el error.

Es necesario configurar los siguientes campos:

- **Código** - Área de texto donde escribir el bloque de código PERL.
