---
title: Environment Loading and Discovery
index: 120
---

To create and map all the Resources needed to finalize the environment model for a Clarive implementation, we recommend
performing any of the following activities:

- Probe and discover infrastructure using rules.
- Load Resources from a database or spreadsheet.
- Duplicate configuration from/to current models.

### Discovery

To discover environments, use Clarive's Probe Operations to set up discovery logic that will detect and load
infrastructure resources from your network.

Steps:

- Create a new rule of type `Action` and select where the action will be available.
- Add probe operations that suit the type of Resources you wish to discovery. Probe operations available depend on the
  plugins and features installed at your installation.

### Loading Resources

Loading Resources into Clarive can be done in three ways:

- Importing CSV, YAML or JSON file.
- Calling a webservice.
- Importing a snapshot

#### Importing from file

Use the `Import` menu option for each Resource grid available to import info.

#### Calling a Clarive Webservice

Calling into the Clarive API using a webservice is another method of loading (and updating) Resources in the system.

Write a webservice rule in the `Rule Designer` to create and load Resources.

#### Importing a snapshot

It is possible to import the Resources through the option Snapshots located in the Administration menu.

More info [here](/admin/snapshot).
