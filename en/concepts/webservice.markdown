---
title: Webservice
index: 5000
icon: rule-webservice
---

In Clarive, a webservice is a type of [Rule](/concepts/rule) that can be called from outside Clarive.

Webservices are the preferred way of automating Clarive operations from the outside world.

Instead of calling API primitives directly (e.g. "create a topic"), we recommend creating a webservice rule that creates
a [Topic](/concepts/topic).  This is in turn called from the command line or from other applications and services.
