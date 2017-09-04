---
title: Release Pipeline Automation
index: 800
---

Release Pipeline Execution Clarive Rules can support three key phases in the delivery process: PRE, RUN, POST. During
the PRE phase, the PREparation for delivery steps are documented and automated. During this phase, typically the
following actions are modeled:

- Environment building/provisioning.
- Binary building: compilation from associated revisions across the various platforms.

Upon completing the build step, the RUN step takes place, which is when the system starts operating within the job
schedules (release windows) for each environment. During this phase, depending on the various natures/types of binaries,
executables and data are placed into the right target environments.  This is done either through SSH, or Clarive Push or
Pull agents, depending on customer topology and architectural constraints.

During the POST phase, Clarive can orchestrate the post deployment activities, such as cleanups, CMDB updates etc.

A Clarive [Rule](/concepts/rule) makes use of environment variables. These variables have specific content for each
environment and allow the **same** deployment Rule to be used across every environment and platform.

This capability allows Clarive to be used to validate and test the deployment logic (simply as code) across every
environment. Clarive allows organizations to test the build, deploy, provision, and test logic across every environment
from a **single** Rule. On top of that, every Rule is governed by version control and change tracking, which provides
extra value for agility and control.

During Rule definition, Clarive allows the Rule Designer to define and document the rollback strategy per line entry at
the same time.

## Pipeline Recreation

Pipeline recreation is the ability to rerun a deployment using a previous version of environment models and overall Rule
logic.

To recreate a previous version, select the `Rule Version` in the `New Job` panel. By default the Rule version is always
the latest.

### Tagging Versions

To know what configuration versions are best, simply tag the Rule versions in the `Rule Designer` interface, under the
version button for the Rule.

### Pipeline Version Storage

Versions are stored in the system according to the capped collection size `rule_version`. Simply modify the capped
collection size to hold more or fewer configuration versions, according to your storage availability and organizational
policies.

### Job Version Snapshot

Clarive automatically stores snapshots of the job contents that were used to deploy a release to production
environments. Simply check the `Snapshot Environment` checkbox in the Environment Resource of your production
environment.
