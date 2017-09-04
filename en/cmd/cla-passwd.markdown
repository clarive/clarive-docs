---
title: cla passwd - Password encryption
index: 5000
icon: console
---

`cla passwd`: Conversion tool for password encryption.

Subcommands supported can be displayed with the help option:

    >cla help passwd

    USAGE: cla [-h] [-v] [--config file] command <command-args>

    cla help <command> to bring up all subcommands.
    cla <command> -h for command options.


`cla passwd`:

- *-u <\username>*: User name for which the password is to be encrypted is a required parameter and may be defined as an
  input parameter:
- *-p <\password>*: User password.
- Typed from the keyboard when command prompts for it.

Encryption is performed using parameter *decrypt_key* or *dec_key* from config file.
