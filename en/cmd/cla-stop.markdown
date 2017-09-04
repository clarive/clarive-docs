---
title: cla stop - Stops all server processes
index: 5000
icon: console
---

`cla stop`: Stop all server processes. It tries to stop all systems Clarive needs to operate.

They are:

- *mongo*: Stop mongo server.
- *nginx*: Stop nginx server.
- *Clarive web server*: Stop web server, options can be sent as arguments to the command to stop web server in some way.
- *Clarive dispatcher*: Stop dispatcher server, options can be sent as arguments to the command to stop dispatcher in
  some way.

This command supports some options. They are:

- `--no_mongo`: To not stop mongo server.
- `--no_nginx`: To not stop nginx server.
