---
title: Rule Profiling
index: 5000
icon: rule
---

Rule profiling allows monitoring and analysis of a job's performance, as well as that of the rule running the job. To
this end, a series of metrics have been included that enable run time monitoring for each rule and job element.

# Configuration

By default rule profiling is switched off since it can affect the performance of the rule. The following configuration
options are available:

- `config.rules.profiling.ids` - choose rules by ids;
- `config.rules.profiling.types` - choose rules by types.

For multiple values separate them by commas.

# Rule

A new option has been included in each one of a rule's services, whereby the user is able to view the number of times
a service has been run, along with averages and minimum and/or maximum values, in other words, its slowest and fastest
run speeds.

Moreover, a graph may be viewed showing run times resulting in a time graph in which element run time performance may be
observed.

This data may be accessed by simply right-clicking on the chosen element, and going into its `Properties`. A new tab
entitled *Profiling* will appear in a new window, showing the above-mentioned values.

# Job

Conversely, a new tab has been included in the job detail in which run time is observed for each rule element involved
in the job. Clarive will display a circular graph showing the time taken by each element.

In addition, a table is displayed at the bottom with the operations run in the job, together with their various times:

### Step

Displays the job steps.

### Operation

This displays the operations that have been performed. It will also be shown in parentheses within them what type of
operation is being performed, which then appears in the top graph.

Furthermore, a first *idle* line is displayed, showing how long the job has been waiting.

### Average

This shows average operation time. If the operation has been run only once, it will display how long it has taken to
run.

If, however, the operation is in a loop and has been run more than once, the average time it has taken to run will be
displayed.

### Execution

This shows the number of times the operation has been executed.

### Exclusive Time

This displays the time the operation has taken to run.

### Inclusive Time

This displays the time the operation and its nested operations have taken to run.
