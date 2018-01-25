---
title: Common Command-Line Options
index: 3000
icon: console
---

This are the common, global command-line options.

Some commands may not use them internally, so it doesn't apply necessarily to every command, but it does get loaded by
the main Clarive `cla` command manager.

### -c [config_file]

This option sets the config file to be used, ie.  the option `-c mypersonal` will tell `cla` to load
the configuration options from any file called `CLARIVE_BASE/config/mypersonal.yml` in the config search hierarchy.

!!! important
    In previous Clarive versions this was known as the `--env` argument and was called _environments_, but for
    better standard it has been renamed, although the `--env` argument is supported as well for legacy reasons.

### --enable-plugins

This flag indicates if Clarive should load plugins at initialization.

Use `--no-enable-plugins` to prevent Clarive from loading plugins from the `init/` directory at startup.

### --debug

Turns on reporting debug messages to the log file.

### --trace [n]

This option sets the trace level
for debug messages.

### --base [path]

Sets a different `CLARIVE_BASE` environment variable.

Setting it here overwrites setting it as an environment variable.

### --home [path]

Sets a different `CLARIVE_HOME` environment variable.  By default `CLARIVE_HOME` is set to `CLARIVE_BASE/clarive`.

Setting it here overwrites setting it as an environment variable.

## Setting options in the [env].yml config file

All the options here can be set also in the `[config].yml` file, except the `-c` option for logical reasons.

For example, this could be an `[config].yml` config file.  All options with dash `-` in the name need to be translated to
underscore `_`:

```yaml
debug: 1
trace: 2
load_plugins: 0
```
