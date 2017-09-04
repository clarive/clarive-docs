---
title: Create Root-Cause Analysis
index: 5000
icon: page
---

[Root-Cause Analysis](/concepts/root-cause-analysis) is a means of resolving problems by identifiying their causes. In
order to perform an analysis you need to follow a series of simple steps.

First you need to add a new daemon *service.root_cause_analysis.daemon* in the [Daemons](/admin/daemon) section. Once
this is added and activated, you need to create a 'Root Cause' Resource in which the Resource Name, Severity,
Interpretation of the problem (a heading), Guidance (which elaborates of the problem) are defined, along with a regular
expression which defines the message with which the Root-Cause Analysis is to be activated.

As an example we shall create a Root-Cause Analysis for when the connection is lost with the destination machine when
sending a file remotely.

We first need to define the Resource:

- **Name** - Loss of connection
- **Severity** - High
- **Interpretation** - The connection was lost
- **Guidance** - Could not connect to the remote machine. Check that the service information is correct, that the
  machine is connected to the Internet and that the firewall is deactivated.
- **Include** - Could not connect

We then indicate the rule service in which the analysis is to be activated. In order to do this, we go to the rule, and
then to the rule's properties (by right- clicking on the service and then clicking Properties). When properties open
there appears a "Root-Cause Analysis" tab containing a combo for specifiying the Resource.

Once these three items have been configured (daemon, Resource and service) the analysis is now ready. Each time the Job
log displays the regular expression indicated in the Resource (*could not connect*), Resource information will be
displayed; severity, interpretation and guidance. This analysis is displayed both in the Log summary and in the log
detail. If it does not appear in the log detail, make sure you have the window configured for displaying Debug messages.
