---
title: Blueprint Rules
icon: rule
index: 1400
---

Blueprints are Rules (Admin/Rule Designer) that allow us to model systems and
Environments on the basis of variables which are grouped/conditioned by
Environment.

In the example below, we have two environments: PROD and TEST. Each of these
contains one or more GROUPS, which have been renamed SERVER_1, SERVER_2 and
SERVER_3, respectively, and reference pre-configured servers e.g. GenericServer
(Resources/GenericServer).

<img src="/static/images/docs/blueprint/blueprint.png" style="width: 308px; height: 485px" />

Each of these GROUPS contains a series of variables, which in turn contain
configuration data for the respective servers referenced by SERVER_1 and so on.

Below is a model representation based on the rule created, illustrating the two
environments mentioned above, and the servers within them, and in turn the
variables containing their respective configuration:

The aforementioned variables are created and configured in Resources/Variables.

Blueprints are in turn specified within Natures (Resources/Natures) via the
newly created _Blueprint_ combo.

This enables Blueprints, along with any servers (and their configuration), file
paths etc. to be passed easily to Projects. Grouping variables in this way
streamlines the process of configuring Projects, which previously had to be
performed manually for each Project.

<img src="/static/images/docs/blueprint/blueprint2.png" style="width: 711px; height: 231px" />

Within Projects we can control which variables are available in which
Environments e.g. an Amazon server that is only accessible within PROD.

<img src="/static/images/docs/blueprint/blueprint3.png" style="width: 336px; height: 398px" />
