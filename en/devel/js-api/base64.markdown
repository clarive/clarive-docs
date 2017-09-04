---
title: cla/base64 - base64 encoder
index: 5000
icon: page
---

Clarive the *base64* method allows you to encode and decode the string passed to the function in base 64. It uses the following two methods:

## base64.encode64()

The encode64 method will encode the input string to obtain the resulting encoding in base 64.

```javascript

var base64 = require("cla/base64");
var string = "123";

base64.encode64(string);

```

## base64.decode64()

The decode64 method will decode the input string to obtain the resulting decoding in base 64.

```javascript

var base64 = require("cla/base64");
var string = "123";

base64.decode64(string);

```
