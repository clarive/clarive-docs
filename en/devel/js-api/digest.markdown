---
title: cla/digest - String based encoder
index: 5000
icon: page
---

In Clarive *digest* method allows to encode any string to generate a unique ID (md5 or sha1) using one of the following
methods:

## digest.md5()

MD5 options creates a 32 digits encoded string using the MD5 hash generator.

This method uses always the same algorithm to generate the strings so for the same entry, user always obtain the same
encoded string.

```javascript

var digest = require("cla/digest");
var string = "123";

digest.md5(string);

```

## digest.sha1()

SHA1 options creates a 40 digits encoded string using the SHA1 hash generator.

This method uses always the same algorithm to generate the strings so for the same entry, user always obtain the same
encoded string.

```javascript

var digest = require("cla/digest");
var string = "123";

digest.sha1(string);

```
