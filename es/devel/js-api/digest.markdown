---
title: cla/digest - Codificador de strings
index: 5000
icon: page
---

En Clarive el método *digest* te permite codificar cualquier string para generar un ID único (md5 o sha1) mediante uno
de los siguientes métodos:

## digest.md5()

La opción md5 crea un string codificado de 32 dígitos de un string origen utilizando el generador de hashes MD5.

Este método utiliza siempre el mismo algoritmo para generar los strings codificados de modo que para la misma entrada,
se obtiene siempre el mismo string codificado.

```javascript

var digest = require("cla/digest");
var string = "123";

digest.md5(string);

```

## digest.sha1()

La opción sha1 crea un string codificado de 40 dígitos de un string origen utilizando el generador de hashes SHA1.

Este método utiliza siempre el mismo algoritmo para generar los strings codificados de modo que para la misma entrada,
se obtiene siempre el mismo string codificado.


```javascript

var digest = require("cla/digest");
var string = "123";

digest.sha1(string);

```
