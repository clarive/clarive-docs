---
title: Infrastructure Pipeline
index: 5000
icon: dashlet-pipeline-infrastructure
---

The infrastructure pipeline dashlet shows how resources defined for the different projects are distributed in the
different environments and related to releases, changesets and revisions.

This resources are defined by creating resources variables and assign them to a project in an environment other than 'Common'.

There are a list of elements can be configured in the dashlet:

### Height in canvas rows

Defines the height in number of rows given to the dashlet.

The height value will be between 1 and 4 where 4 will occupy 100% of the page.

### Width in canvas columns

Sets the width that the item will occupy in the dashboard.

The maximum allowed value is 12 (100% width).

### Autorefresh

Allows to make the dashlet more dinamic adding an automatic refresh (in minutes).

#### Mode

- `Release` - group dashlet content by releases
- `Changeset` - group dashlet content by changesets
- `Revision` - group dashlet content by revision

#### Filter by Customer Resource

Select resources that match Clarive classes

#### Filter by Customer Role

Select resources that match Clarive roles

#### Filter Variables

Select resources that match user defined variables

#### Environments

Select which environment columns to show (or hide).

### Revision field

Specify the ID of the revision fieldlet that belongs to the selected categories (this ID must be the same for all of
them). It will be needed to visualize data in Revisions mode.

#### Exclude Selected Environments

Negate the selected environments so they are hidden.

#### Select topics in categories

Select the topic categories to include. Allow categories are changeset-type ones.

#### Exclude selected environments

Negate the selected categories, so they are hidden.

#### Advanced JSON/MongoDB condition for filter

This is a space for an additional MongoDB filter to be added, which will be applied to the topic.
