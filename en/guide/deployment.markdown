---
title: Deployment
index: 200
---

Clarive implements a considerable amount of useful features for continuous and discrete deployment modes. Clarive
deploys revisions from change providers.  Change providers are typically code or artifact repositories (i.e. Git,
Subversion or Nexus) but could also be Salesforce or a database.

As part of implementing automated deployment at your organization, you must plan for the following:

#### Applications

Select a set of target applications for this implementation

#### Technologies ("Natures")

Define the technologies that will be deployed (from a set of target applications or services)

In Clarive, these are called *Natures*.

#### Deployment and Rollback Logic

Collect all information on current automation logic being used, or manual processes in place.

With this information at hand, you are now ready to write automation rules.

#### Resources (CIs)

Determine all resources and environments used by the target applications and Natures for each configuration environment.

Write environment models for the patterns implemented at your organization.  This will help later with onboarding new
applications as they join the automated delivery flow implemented in Clarive.

## Deploying Topics

Clarive deploys Topics. Topics contain the revisions to the configuration being deployed. Clarive can deploy two types
of Topic:

- Changesets
- Releases

The way in which releases are packaged can vary by application type and organizational methodology. Clarive supports
top-down as well as bottom-up release management and packaging. This way, Clarive can support both traditional as well
as agile methods.

### Deploying Changesets

Clarive has multiple ways of "packaging" builds and deployments. The first type is a Changeset where various revisions,
which can come from ANY revision repository, and can be related/linked into. Once within a Changeset, anyone with the
right permissions can click on the revision link and can see the revision details directly from within Clarive. There is
no need to go outside the tool.

Changesets can be built and deployed when triggered by a status change, a Job run, or an internal or external event.
Based on the different Natures within the associated revision, the build (and/or deployment) rule will execute the
appropriate actions to build, stage, test and/or deploy to the correct environment.

### Deploying Releases

Clarive also has another way of "packaging" builds and deployments: a release-type topic. This type allows changesets or
releases to be combined into another level of logical packaging. When such a "release" is built and/or deployed, then
Clarive will perform the operation for all revisions that are part of the release, at any level further down in the
hierarchy.

This way, any type of composition can be formed and managed.

Changeset and Release are just two examples of possible discussion topics part of application delivery, but can define
as many as required to orchestrate the delivery process as needed.
