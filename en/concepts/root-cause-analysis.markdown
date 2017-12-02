---
title: Root-Cause Analysis
index: 5000
icon: page
---

Root-Cause Analysis allows the addition of custom high level descriptions to the different job operations. In particular
it can be used to give a meaningful explanation to the user when a job error happens.

In order to use it, several things have to be configured:

1. Root-Cause [Resource](/concepts/resource) with description and matching patterns.
2. All [rule](/concepts/rule) operations that can be analysed must be configured with the previously created Resources.
3. Root-Cause Analysis [Daemon](/ee/admin/daemon) has to be running in order to process the jobs.
