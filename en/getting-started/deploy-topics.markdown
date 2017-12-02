---
title: Deploying Topics
index: 5000
icon: job
---

In order to deploy a Topic in Clarive, its Status must be set to one that is defined in the corresponding Category's
[workflow](/concepts/workflow) as deployable. The Topic must also be associated with a [Project](/concepts/project).

Click on `New Job` and select the appropriate Transition, which will open the New Job tab.

The *Transition* combo will display the Transition selected.

Select from the *Pipeline* combo the Pipeline Rule you wish to use to deploy the Topic.

The *Version* combo offers the option of the latest version of the Pipeline Rule, in addition to one or more tagged
versions of it where previous versions have been tagged (see [Rule Designer](/ee/admin/rule-designer)). Each tagged version shows
the names entered in the tag, followed by the User name in brackets. This offers the possibility of reverting back to an
earlier version of the Pipeline Rule in the event of an error occurring in the latest version.

The *Dynamic tags (version is calculated during execution)* checkbox appears on selection of a tagged version of the
rule. When checked (which it is by default), it detects the version of the rule last tagged with a particular name.
Otherwise, it retains the version that was tagged at the time of selection in the *Version* combo.

*When* allows selection of Date and Time for deployment, which references the [Job Calendar](/ee/guide/calendaring) to find
an available slot.

The Calendar may be overriden by checking *Create a job outside of the available time slots*. This makes adding
a comment in the otherwise optional *Comments* box mandatory.

The *Job Items* box contains the job items to be deployed, in this case the Topic from which we opened *New Job* and
associated Topics.

Click `Create` to create the Job. The progress of the Job may be tracked in the [Monitor](/getting-started/monitor).
