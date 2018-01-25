---
title: Pipeline Rules
index: 2000
---

Pipeline rules are triggered during Clarive CI/CD:

- __Continuous Integration__ - run for every topic branch pushed while the topic is
  __In Progress__

- __Nightly builds__ - pipeline jobs run for release branches every night

- __On-demand deployment__ - run on-demand requests by the user to deploy a topic
  to an environment.

For each one of the above CI/CD run events, Clarive may kickoff one or more events.

Here's the skeleton of a pipeline rule:

```yaml

build:
   - ...

test:
   - ...

deploy:
   - ...
```

## Job Contents

For every pipeline there are be different contents.

Clarive is a multi-project, multi-repository system, which basically means
that a single job can deploy many applications and their components at once.

Pipeline                    | Contents
----------------------------|-------------------------------------------------------------------------
Continuous Integration      | A single project, repository and topic branch
Nightly Builds              | Multiple projects, repositories and release branches
On-demand Deploy            | Multiple projects, repositories, releases and topic branches

## Job Environment

Every job runs against an environment. Environments are defined typically
with uppercase letters.

You pipeline rules can be called from any environment.

To get the current environment in which your rule is being run,
use the job context object `ctx.env()`

```yaml
deploy:
 - echo: "This deploy is running for environment {{ ctx.env() }}"
 - if: "{{ ctx.env() == 'PROD' }}"
   then:
   - shell:
       host: prod.server
       cmd: rm -rf /bea/user_projects/domains/yourdomain/servers/yourserver/tmp
```

## Job Items

Job items are the list of files that have changed when compared with
the current job environment.

The comparison is done by Clarive using the environment tag position
for every repository.

```yaml

# lets not copy the full website every time

deploy:
    - foreach: "{{ ctx.job('items') }}"
      do:
         - ship:
             file: ${it}
             host: web.server
             to: /var/www/
```

## Execution

The first thing to remember is that all job rules __run on the Clarive server__.

Before getting to execute rulebooks, Clarive will checkout files locally.
Every rulebook op in a pipeline rule __will start with all its correct branches
cloned__ so that no git operations should be necessary.

1. A user event triggers a job. The job is put in the queue.

2. The job is picked up by the Clarive job daemon in the Clarive server.

3. A temporary directory in the is created.

4. Clarive will clone a copy of all the Git
repositories locally so that the rule has at its disposal all of the necessary
repositories checked out at their corresponding branch and correct HEAD.

4. For each project repository cloned, Clarive will run its corresponding
rulebook `clarive.yml`, if any.

5. First all `build` rules are run. Then all the `test` rules. If the job is
scheduled for a later time, it goes into hybernation until being waken up for
the `deploy` rules.

## Scheduled jobs

On-demand jobs can be scheduled by the user to run at a later date.
Scheduling only affects the `deploy` rule. That's because most of the
time, we want to build and test as soon as possible, and deploy at a later
time. So `build` and `test` always run as soon as it's picked up by the
job queue.

Continuous integration and the nightly build pipeline don't fall into the
scheduled job category though. CI pipelines run as soon as possible after the
user pushes a topic branch, while Nightly pipelines runs all the rules at
nightly schedule.

That means the job will run the `build` and `test` rules right away
and run the `deploy` rule at the scheduled time.

## Available events

As mentioned before, there are 3 basic events that get triggered
during a pipeline:

### `build:`

Build is run once for every repository in the job contents.

The build rule starts as soon as the job is created and picked up by the queue.

### `test:`

Test is run once for every repository in the job contents, after
all the build rules have run successfully.

The test rules exist so that we can start testing only after all
building has finished.

### `deploy:`

Deploy runs once for every repository included in the job, just like `build` and `test`.

## Filtering Rules

You can filter when your rule will run by adding scope
variables at the top of each event entry.

- `environments`
- `branches`

```yaml

# limit build to feature branches only

build:
   branches:
      - feature/*
   do:
      - cd myproj/src/
      - go build main.go

deploy:
   environments:
      - Testing
      - Staging
      - Production
   do:
      - ship:
          host: ${hostname}
          from: myproj/
          to: /opt/myproject/bin/
```

### `build_*`, `test_*`, `deploy_*`

You can also create secondary events that will get triggered during their corresponding
primary event:

```yaml

# triggered during a build event:

build_feature:
   branches:
      - feature/.*
   do:
      - g++ src/*.cpp

build_hotfix:
   branches:
      - hotfix/.*
   do:
      # lets build faster
      - g++ -O0 src/*.cpp

# triggered during deploy:

deploy_feature:
   branches:
      - feature/.*
   do:
      - ...

deploy_hotfix:
   branches:
      - hotfix/.*
   do:
      - ...

```

Or separate your build types according to the job environment:

```yaml
build_CI:
    environments:
      - Integration
    do:
      - ...

build_CD:
    environments:
      - Testing
      - Staging
      - Production
    do:
      - ...
```

## Available Context

With every job pipeline the rulebook engine makes a set of useful context
variables is available for importing into the job.

```yaml
build:
   - dist_dir =: ".artifacts/{{ ctx.job('environment') }}/dist/"
   - mkdir -p {{ dist_dir }}
   - touch {{ dir_dist }}/{{ ctx.job('name') }}
```

For a list of all context variables, read the [context data doc article](/rulebook/context#ctxjob).
