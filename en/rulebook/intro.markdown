---
title: Introduction to Rulebooks
index: 100
---

Rulebooks are the file-based automation language of Clarive.

Every functional aspect of the system can be automated with rulebooks, from
CI/CD pipelines (used to build, test and deploy applications), to form,
workflow and dashboard customization.

Rulebooks are files that define rules. Rules are sets of actions that are
triggered on certain system events. The system events include things like
build, deploy in job pipelines, promotion and demotion of topics in a workflow
and others. So we stretched the concept of an `event` to include any place you
can hook code into.

## Where to use Rulebooks

Rulebooks can be used in 2 places in Clarive:

- `.clarive.yml` and other project based YAML files
- in the REPL, for testing

## Yet another YAML

Clarive rulebooks are inspired by the computer languages used to automate
systems work, from Bash to Python. We think automation requires a little more
than a simple declarative language, so rulebooks aim to be a turing
complete imperative language based on YAML, and not a rigid data structure
layed out in a markup language.

```yaml
do:
   - foo = shell: git branch -a
   - echo: your branch is {{ foo.output }}
```

However, we are conscious that coming up with yet another language in an
already diverse, maybe even crowded, computer language space is a stretch.
That's why rulebooks are meant to be glue code for other languages.

You can (and should) write minimalist rules. Even though rules can
have a lot of logic.

## Key Rulebook features

- loops (`for`) and conditional (`if`)
- variables
- send and import files
- read/write config files
- run local and remote system commands

## The Environment

Where are rulebooks being run?

Clarive is a centralized system. All rulebooks run from within the central
server. Rulebooks __are not shipped to workers, agents or nodes in general__.
They are meant to run from the central Clarive server (in fact, from where the
[Dispatcher](/concepts/dispatcher) is installed).

Depending on the event being fired, the environment will be one of two
possibilities:

- a disposable pipeline job directory, created for each job the system runs
- a stable workspace directory

All necessary files needed by your `.clarive.yml` should be inside git
repositories managed by Clarive.

## Ops

_Ops_ is a short for _operations_. "Ops" is how the Clarive rule language instructions are called.
Here are some examples of rule ops:

Language or control ops:

- `var` - variable assignment/declaration section
- `def` - define your own ops using YAML
- `import` - imports modules as ops into your rulebook
- `import_vars` - imports variables from the upper calling scope
- `if` - conditional
- `for` - loop variable contents.
- `try-catch` - catch errors

Service ops:

- `ship` - send a file to a server
- `fetch` - bring a file back from a server
- `parse` - parse a string config template or file
- `dump` - dump a data structure
- `print` - print string or data structure
- `echo` - print string followed by a newline
- `email` - send an email to users or addresses
- `slack_post` - post a message to slack
- and many, many more...

Actually, the list of installed ops in your system may vary according to the
plugins you may have installed. Check out the [rulebook api
reference](/rulebook/api) for the official list of ops (which does not include
plugin ops).

For a complete reference __for your Clarive installation__ open the help
document in your server at:

     https://yourclariveserver/r/help?path=/rulebook/rulebook-api

## YAML language features

Rulebooks are valid and perfectly legal YAML, or at least to what commonly
established as lega. No special parsing is performed by the Clarive YAML
parser, which is based on LibYAML.

## Variable and templating

Rulebooks can make use of a variable replacement and
templating system based on ClaJS, a very fast Javascript
interpreter that comes bundled with Clarive.

- `${myvar}` - simple variable parsing
- `{{ myvar }}` - Javascript variable parsing

Javascript templating with what is know as handlebars (`{{ .. }}`)
is a very powerful tool for dealing with complex data.


## Calling out to your favorite language

One of the most useful aspects of rulebooks is that they can turn any
program into an op.

## Hello World

To try out the rulebook language, head over to the [REPL](/concepts/repl).

```yaml
do:
   - echo: hello world
```
