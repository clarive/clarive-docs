---
title: Project Pipeline
index: 5000
icon: dashlet-project-pipeline
---

The project pipeline dashlet shows how releases and changesets are distributed in the different environments.

#### Mode

- `Release` - group dashlet content by releases
- `Changeset` - group dashlet content by changesets
- `Revision` - group dashlet content by revision

#### Environments

Select which environment columns to show (or hide).

### Exclude Selected Environments

Negate the selected environments so they are hidden.

#### Select topics in categories

Select the topic categories to include. Allow categories are changeset-type ones.

#### Advanced JSON/MongoDB condition for filter

This is a space for an additional MongoDB filter to be added, which will be applied to the topic.

#### Label Mask

This is the text shown in each of the releases or changesets listed.

The variables available are:

- `${category.name}`
- `${category.acronym}`
- `${category.color}`
- `${topic.mid}`
- `${topic.title}`
- `${topic.[field name here]}`
