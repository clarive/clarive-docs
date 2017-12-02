---
title: Rule Concepts
index: 100
icon: rule
---

Rules are the core of how Clarive works.

Rules define how the system behaves when events occur,
how to build, test, provision and deploy applications
and is used to customize the aspect and behaviour of
workflows, forms and dashboards among others.

Rules are the central hub for customizing
Clarive. Unlike other tools, our intention is to prevent
customization to happen from the outside. Clarive customization
should happen from within.

Rules are algorithms which are touring complete.
They look like computer programs, but are easier to read
through and understand because every instruction
of the program is an _operation_, "op" for short.

### A DevOps IDE

Rules are defined, checked and tested using the
powerful Clarive [Rule Designer](/ee/admin/rule-designer).

The rule designer holds all the rules defined in the system.
In the rule designer we not only design our rule logic, but
also run tests and verify rule quality. For this reason,
the rule designer can be compared to a full-blown IDE.

The Clarive rule designer palette offers hundreds of
operations -- some of them available after installing with Clarive plugins and
features. The operations in the palette can also be extended with
plugins that register new palette ops.

### Forget Flowchart Diagrams

We prefer rules, and their tree-like nature, to flowcharts.
Customization logic can get VERY large quickly, and there's
nothing easier to navigate than nested trees that can reasonably
fit into a computer screen. Flowchart-like automation
canvas are only good for simpler automation directed at
non-technical users. Clarive users on the other hand are used
to code and scripting to a certain extent.

Flowcharts are great for computer science classes and
mostly died in the 90s, together with CASE and UML tools.
Did you ever wonder where have flowchart-based tools from
the past gone?

### Forking and branching

Although they are decision trees (nested structures), rules
can fork and branch, running process in parallel.

Just pick any operation in the rule and apply the
fork option in the op properties.

### Massively Parallel

Rules run concurrently across Clarive.  They can run on as many servers as you
want. Just install the Clarive server software in each one and start a
Dispatcher daemon. The Dispatcher will start and supervise the event queue
that runs rules (actually they are event rules).

### Concurrency Control

Rule ops can have critical zones with no concurrency. These are called
[semaphores](/concepts/semaphores) in Clarive lingo.

Use semaphores in rules to control how many parallel rules
can run a certain op simultaneously.

### Event-based

Rules are ideal for event-based triggering. When
X happens, do Y. Define event rules to trigger your
rule logic everytime an event happens.

### Avoid Duplication

Use independent rules to structure your common code into
independent fragments. That way we can avoid duplicating
logic everywhere.

Independent rules can be called with parameters.

### Variable Templates

Rules can make use of variables to configure and customize
operations being run. Variables can be set at
global, environment or project levels.

Variables are composable: variables can contain variables.
Their values get deparsed and filled out dynamically by Clarive
so that many levels of templating is possible.

### Rule Serialization

Rules keep their state in something called a [Stash](/concepts/stash).

Stashes can serialize the state of the rule to the database and
back, greatly simplifying the way rule state is managed.

### Put Code in Rules

Rules can hold code snippets, for greater flexibility.
Rule code can be written using the Clarive JavaScript DSL, [ClaJS](/devel/clarive-js).

Use code snippets for the greater coding feats that cannot be accomplished
with the many operations available in the palette.

### Other rules

- **Report** - Create a report with rule code. For more information, there is a how-to called [Create
  a report](/ee/how-to/create-reports).
- **Webservice** - Allows to integrate webservices in rules.
- **Workflow** - Allows to create a workflow with rules. To make it work, the rule should be included in the category
  configuration.
- **Independent** - Little rules to include within more complex rules, simplifying the system.
- **Dashboard** - Rule that allows the user to create a personalized dashboard with dashlets components.
- **Form** - Rule composed by fieldlets that shape the form of a topic.
- **Blueprint** - Rule composed by variables and when assigned to nature builds project variables form.

### Stash

The Stash of the rules is Clarive system that keeps the state of the pass between runs. Stash variables are used to
communicate between tasks and it is used to replace the variables in the different configurations.
