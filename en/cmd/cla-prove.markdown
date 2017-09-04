---
title: cla prove - Run internal testing
index: 5000
icon: console
---

`cla prove`: runs system tests and checks their results.

This command executes all test files located in the core test directory and displays the results on screen.

Each test case starts with:

`[start] <test case name>`


and ends with:

`[end] <test case name> [<duration_of_the_test>]`


In case of error, the output shows the error message in red.

This command accepts the following options:

- `<directory_or_path>` - Passed as an argument to the command, executes only the core tests defined under
  …/t/<directory_or_path>.
- `--features` - Executes tests for all features.
- `--plugins` - Executes tests for all plugins.
- `--feature <feature_name>` - Executes tests for the feature <feature_name>.
- `--plugin <plugin_name>` - Executes tests for the plugin <plugin_name>.
- `--all` - Executes all features, plugins and core tests.
