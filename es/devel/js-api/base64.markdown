---
title: cla/base64 - Codificador base64
index: 5000
icon: page
---

En Clarive el método *base64* te permite codificar o decodificar en base 64 el string que se le pase a la función. Los dos métodos que tiene son:

## base64.encode64()

El método encode64 codificará el string entrante para obtener el resultado de la codificación en base 64.

```javascript

var base64 = require("cla/base64");
var string = "123";

base64.encode64(string);

```

## base64.decode64()

El método decode64 decodificará el string entrante para obtener el resultado de la decodificación en base 64.

```javascript

var base64 = require("cla/base64");
var string = "123";

base64.decode64(string);

```
