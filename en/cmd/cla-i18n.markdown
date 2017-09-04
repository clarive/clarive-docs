---
title: cla i18n - Runs translation generator
index: 5000
icon: console
---

`cla i18n`: Searches translatable strings to be entered into the code. This includes the new strings in the localized
translation files in the core directories.

It takes the following options:

- `--core` - Runs an automatic search for strings in the core.
- `--features` - Runs an automatic search for strings in all features.
- `--plugins` - Runs an automatic search for strings in all plugins.
- `--plugin <plugin_name>` - Runs an automatic search for strings in the plugin or feature <plugin_name>.
- `--all` - Runs an automatic search for strings in all features, plugins and core.
