---
title: Releasing
index: 400
---

Releasing a new version of an application, configuration or infrastructure in Clarive is done by executing the given
release (or changeset) Topic as a **[deployment](/ee/guide/deployment) Job**.

This **Job** executes a combination of all automatic tasks and orchestrates all the manual tasks needed to deploy
a release.

## Release Strategies

Releasing can adapt to a set of strategies:

- Big-bang releases.
- Gradual releases.
- Stepped deployment.

#### Big-Bang Releases

Deploy all of the changesets at once in a single Job.

This is the best strategy for production environments, because it makes changes "transactional". This means Clarive
guarantees that it can roll back the full Job in case of failure.

To implement big-bang releases:

- Add "Bind Releases" in the Status Resource where you want to avoid deploying gradual changesets, i.e. `Production`
  status.
- Develop a Job pipeline Rule that takes full advantage of Job rollback strategies.
- If necessary, add manual deployment ops to your deployment Rule: approvals, pauses, etc.

#### Gradual Releases

Gradual releases mean deploying changesets individually into an environment.

This strategy is typically better suited for preproduction environments.  The main advantages is that we can *cherry
pick* releases that are going to be deployed into an environment.

#### Stepped Deployment

This means that the gradual release steps are implemented through pauses, traps or approvals during the deployment Job.

We recommend using stepped deployment if the release execution not going to take more than 24 hours.

Having a Job running for over 24 hours means having the job processes taking up resources in the Clarive server (and
related targets).

### Calendaring

To schedule release deployments, Clarive uses its calendaring engine to process what can be deployed and when. Use the
`Calendaring` admin interface to define available Job slots by any Scope or Job content:

- Global schedule.
- Environment-based slots.
- Specific dates (i.e. holidays) as exceptions.
- Project or Resource-based calendar slots.

### Release Infrastructure Relationship

Releases and Changesets hold relationship to Resources in the Clarive Graph. This enables, for instance, identification
of which releases may be affected by certain infrastructure outage.

To use the CI Graph dashlet, add it to the Release Topic category Dashboard:

1) Create a new Dashboard Rule in the `Rule Designer` by clicking ![](/static/images/icons/add.svg). Fill out
the `Name` field, and set the `Type` field to **Dashboard**, then click `Done`. Open the newly created Dashboard Rule
and add the `CI Graph` dashlet from the `Palette` by dragging over the name of the Dashboard Rule. Click `Save`.  For
further details, see [CI Graph](/ee/palette/dashlets/ci-graph).

2) Open the `Admin` dropdown, and select `Categories`.

3) Select the *Release* Topic.

4) Select the *Dashboard* created in step 1 from the dropdown menu in the `Dashboard` field. Click `Save`.

Once you open the *Release* Topic, the user can drill down through the related **Resources**, including infrastructure, for
a given environment or project for that release.

#### Deployment Infrastructure

Infrastructure that will be necessary for deploying a release is also available when creating a `New Job`.

### Redeploying a Release

If a release fails, or the environment is rebuilt from the outside, a release can be redeployed to that environment
using either of the following:

- Job rerun.
- Creating a new deploy transition into the environment.

Either way, release will be redeployed to the environment.

#### Job Rerun

By rerunning the job through the *Job Monitor* (select `Jobs`, then `Monitor`), the same variables and values used in
each step will be reused. That means the same version of the configuration will be deployed to the environment.

A Job Rerun also allows the user to control which Job step is going to be re-executed. This allows users to rerun only
the `RUN` phase of the job.

#### Static Redeploy

If the release is already in an Environment (e.g. DEV), and the transition from and to the status exists in the workflow
for the release with `Job Type` **static**, then Clarive can redeploy a release to an Environment where it is already
installed.

To set up static redeploys, edit the workflow for the *Topic* category:

- If it is a simple workflow, activate the `Admin` dropdown menu and select `Categories`, followed by a *Topic*. Then go
  to the *Workflow* tab, and from the `From Status` dropdown, select a workflow transition with *Job Type* **static**
from and to the same status e.g. from QA to QA (click to maximize left-hand Lifecycle bar if minimized, then select
`Resources`, `All`, `status` and *Job Types*. Set `Type` to **Deployable** and click `Save`).
- If it is a Rule workflow, modify the workflow rule so that it has a transition from and to the same status, set
  `Deployment Type` to **static**. Select `Admin`, `Rule Designer` and ![](/static/images/icons/add.svg).  Set
`Type` to **Workflow** and click `Done`. Open the newly created Workflow Rule, and select `Palette`. From there drag the
`Change Topic Status` Workflow over the name of the Workflow Rule. Click on this and set `Deployment Type` to
**Static**, then click `Save`).

### Provision / Decommission Configuration

Using catalog repositories, users can add provisioning tasks to releases changesets.

Provisioning is executed when the Rule executes. Make sure the Rule has a `Provision Task` operation configured at some
point, otherwise no provisioning tasks will be executed.

A good strategy for setting up provisioning during the release process is to setup the deployment during a `PRE` job
step operation to deploy provisioned tasks *before* the scheduled time (`RUN` step).

### Federation After Deployment

Federate important application configuration information with external CMDBs if you have one.

Add webservices and federation calls to your deployment rule that will federate the configuration changes deployed by
your last deployment job.
