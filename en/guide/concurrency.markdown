---
title: Concurrent Deployment and Releases
index: 240
---

Here are some of the use cases that we support for concurrent releases using a combination of the above features:

### Release Planning

A release can be planned and scheduled for an environment; Clarive can report what the planned releases are for a given
environment.

#### Planner

First set up a [Release Planning fieldlet](/rules/palette/fieldlets/environment-planner) so that Release Managers can
enter planned dates that can be scheduled.

#### Visualizations

Use the [Release Calendar dashlet](/rules/palette/dashlets/calendar) for giving visual cues to Release Managers as to
how environments are being planned and what is installed in each environment at a given time.

Use the [Project Pipeline dashlet](/rules/palette/dashlets/project-pipeline) to enable Users to see how projects,
releases and changesets are deployed to each environment.

### Calendaring

Release deployments have to go through Calendaring in order to be able to find an available slot.

Semaphores and priorities can prevent clashes while deploying release application changes and infrastructure into an
environment.

Release Managers can prioritize and control the execution of release delivery through our Job Monitor

### Event Rules

Create event rules for implementing custom logic that limit when and where a Topic can be deployed.

Event rules for Release Concurrency can be triggered at different moments in the release lifecycle:

- When a Release Planning field changes (`event.topic.modify_field`)
- After a release is promoted/demoted into a new status (`event.topic.change_status`)

### Workflow Rules Concurrency Control

Workflow rules can be even more elegant than event rules for managing concurrency.

Workflow rules produce a list of *next statuses* available to a release or changeset (or, in fact, any Topic).

- Add concurrency verification ops in the logic.
- Then use workflow rules to limit the list of transitions available to a Topic.
- Releases and changesets cannot be deployed to an environment unless a transition to that environment exists.

*IF NOT environment_is_busy('QA') STATUS 'QA'*

**NOTE**: One drawback of using workflow rules to allow or deny a transition is that the User will not know why they
cannot transition to the next status (or deploy the topic). In that respect, using event rules is better, because
failure in the rule will show up in the User interface.

### Other Types of Release Concurrent Control

Releases can be rolled-back fully or partially, more information here [rollback](/guide/rollback). Rollbacks are useful
to keep release integrity.
