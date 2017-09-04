---
title: BDD tests
index: 5000
icon: page
---

# Introduction

## BDD

A *Behavior-Driven Development* ​​or BDD is a software development process concerning the field of QA where it
is endeavoured to establish a common language between the technical department and the business department, so that the
common language is taken as a starting point for creating test cases (Scenarios) for fresh development.

Using this method, acceptance testing is defined using user stories (features):

    "As a [role] I would like [X features] for the purpose of [benefits]"

By using the aforementioned sentence, we can describe the acceptance criteria for the user stories by means of the
following Scenarios:

    Given [initial context],
    When [the event takes place],
    Then [expected result]

To summarize, the BDD testing cycle is as follows:

- Writing of user stories.
- Writing of likely scenarios.
- Automation of acceptance testing.

With a view to having a common communication framework among developers, the QA team and business or non-technical
roles, the most important aspect is a common language: Gherkin

## Gherkin

User stories are written by Product owners and people not as technical as developers. In BDD, automation of testing is
what is performed. Aside from having user stories just as performed in a SCRUM methodology, each user story will be
written using a special language, Gherkin, and will be saved in files with the *.feature* extension (generally within
the *ta/* directory).

Gherkin is a language (DSL) that closely mirrors natural language and is easily understood by business and users. The
idea is to describe what the software does, as opposed to how it does it. The language has only five statements:

    Feature
    Scenario
    Given
    When
    Then

These features resemble user stories. Typical of user stories, they need to contain *As*, *I want to* and *In order to*.
For example, for the user story "Tool access":

    Feature: To have access to Clarive Software in order to create Jobs
    As an Administrator
    I want to access Clarive
    In order to be able to perform deployments.

As can be seen in the example, we can also use Gherkin to generate documentation and to automate future testing, which
can be achieved with a language accessible to everyone.

Later on, in order to run tests, we will need a tool that interprets *.feature* files (Cucumber for example). In order
to do so, it is necessary for someone to 'translate' natural language used in these files into code interpreted by the
system.

Before performing this translation, it is necessary to write out the different scenarios associated with each user
story, which provides us with examples of how the system should behave with the development carried out in the story.

These scenarios will be the intermediate step between the user story and the implementing of an automated test.
A scenario describes an example of system behaviour, and these are acceptance conditions of a user story.

A scenario is made up of a series of steps:

    Given (prior condition for the scenario),
    When (execute an action in the application),
    Then (the expected outcome).

If we continue with the previous user story, a scenario would be:

    Given I am the Clarive administrator.
    When I create a Job.
    Then I can track Job progress from the monitor.

It is now necessary to define the scenario. For example, in this scenario typical of BDD tests:

    Scenario: Cutting vegetables.
    Given a cucumber that is 30 cm long.
    When I cut it in halves.
    Then I have two cucumbers.

We could write, using regular expressions for example, the following definition:

    Given qr/cucumber that is "(.*?)" cm long/, sub {
        # The Perl Code goes here
    }

    When qr/I cut it in halves/, sub {
        # The Perl Code goes here
    }

    Then qr/I have two Cucumbers/, sub {
        # The Perl Code goes here
    }

# Installation

The features are run in a Firefox browser by means of Selenium WebDriver.

## Selenium WebDriver

The (*standalone*) server is included in the *local/* directory if, and only if, the Clarive *dev* package is installed.
This package is installed using the`cla stew install clarive-dev` command, which installs both the server and the
necessary Webdriver.

## Firefox

It is necessary for the server on which the tests are to be run to also have the Mozilla Firefox browser installed with
a graphical interface. Generally this browser comes installed by default with most Linux distributions, which can be
ascertained by running the command:

    firefox -v

Should you not have it installed, follow the instructions shown [here <img class='ext-link'
src='/static/images/icons/window-new.svg'
/>](https://support.mozilla.org/en-US/kb/install-firefox-linux).

Once it is installed, make sure that it works and that a new Firefox window opens:

    firefox

### Error:no display specified

If this error message appears, we need to define the environment variable $DISPLAY. There are a number of solutions to
this problem, depending on the operating system. To define the variable $DISPLAY, run `export DISPLAY=:0` before
launching Firefox.

# Use

## Running tests

In order to run BDD tests, we will need to have started the Selenium server:

    java -jar /opt/clarive/local/bin/selenium-server-standalone.jar

Example taken from a standard Clarive installation.

In addition to starting the Clarive server with a 'test' database (it is necessary to create the corresponding .yml
environment file) with the CLARIVE_TEST setting set to '1':

    CLARIVE_TEST=1 /opt/clarive/clarive/bin cla web-start --env test --migrate-yes

Example taken from a standard Clarive installation. The 'migrate-yes' label is optional, although recommended.

It is possible to run all tests at once, to run all the tests in a directory (and its subdirectories), and to specify or
run a particular test. This is done by using the `cla proveui <tests>` command

    cla proveui ta/                            // Runs all BDD tests.
    cla proveui ta/admin                       // Runs all test in the Admin. directory
    cla proveui ta/user-actions/login.feature  // Only runs the tests included in this feature.

They should always be run from path `/opt/clarive/clarive`.

# Structure

## BDD tests

All BDD tests reside in the `ta/` directory. This contains the following structure:

    ├── ta
        └── lib
        └── <area>
            └── <sub_area>
                ├── <feature-file>.feature
                ├── <feature-file>.feature
                ├── <feature-file>.feature
                └── step_definitions
                    └── basic_steps.pl

We can see in the above structure how each area and sub-area of the tool has been divided into directories. Moreover,
each path containing a `.feature` file must also contain a directory called `step_definitions`, which in turn must
contain a file called `basic_steps.pl`.

These `basic_steps.pl` files contain the 'interpretation' of the language. In other words, once the scenario has been
defined in the Gherkin language within the `.feature` file, `basic_steps.pl` will take care of translating every line of
the `.feature` into Perl code in order to run the test.

To summarize, using the previous example. The `ta/test.feature` file would look like this:

    Scenario: Cutting vegetables
        Given a cucumber that is 30 cm long
        When I cut it in halves
        Then I have two cucumbers

Whilst the `ta/step_definitions/basic_steps.pl` file contains the interpretation:

    Given qr/cucumber that is "(.*?)" cm long/, sub {
        # The Perl Code goes here.
    }

    When qr/I cut it in halves/, sub {
        # The Perl Code goes here.
    }

    Then qr/I have two Cucumbers/, sub {
        # The Perl Code goes here.
    }

### Given, When, Then (past, present, future)

In summary, **Given** is used to denote the context in which the scenario is taking place, **When** to show how to
interact with the system, and **Then** to check that the outcome is as expected:

- Given (a context): The *Given* step is used to describe the initial system context, describing the conditions prior to
  the test. Generally, it is something that has occurred in the past, which is why they are usually expressed in the
  past, making indication of these actions more obvious.
- When (something happens): The *When* step is used to describe an event or an action, for example a person interacting
  with the system, and in this case the event will be written in the present.
- Then (expecting something to happen): The purpose of the *Then* step is to observe the outcome, therefore it is used
  to describe the actual or expected results, and the step will therefore be written in the future.

Those less experienced with BDD commonly make the mistake of confusing When with Then, which can easily be avoided by
using verb tenses.

## lib/ directory

There are occasions when steps can become long and complex, and difficult to read for people other than the person who
wrote them. This is why internal libraries are used. Some of the functions are defined within them, with a view to
simplifying the `basic_steps`. These libraries are particularly useful where steps are repeated in different scenarios,
which saves writing code more than once.

Within the `lib/` directory there are two types of file, the `.pm` files, which are standard libraries, and
a`login_steps.pl` file, where all the steps necessary for logging in to Clarive are located.

### Using login\_steps.pl

This file must be included in all `basic_steps.pl` files located in the `ta/` directory. This handles login to Clarive.
It must be included in all `basic_steps.pl` files we develop using `do`:

    do 'ta/lib/login_steps.pl';

### Creating and using libraries

The `lib/` directory contains libraries created specifically for BDD tests. Within `.pm` files there are generic
functions that the user can use in `step_definitons` files. These files are divided into categories, although the
developer is free to create a new one if he or she deems it necessary, observing the naming conventions used in the
existing ones.

All libraries start by defining the library name:

    package TestComponentExplorer;

This will then be used in the `basic_steps.pl` file. Thus, within these files will be the call to the library:

    use TestComponentExplorer;

All functions defined in the library may now be used:

    TestComponentExplorer->node_in_explorer_is_visible('Deliver');

## Using Databases

In order to run tests, there are predefined databases available, and the following are a few examples:

    TestPermissionsTopicFields.pm
    TestPermissionsTopic.pm
    TestPermissionsUser.pm

These files are located within the path:

    /opt/clarive/clarive/lib/Baseliner/SetupProfile/

Example taken from a standard Clarive installation.

Each of these must contain what is needed to test the different areas and functionalities of the tool. Should it be
necessary to add a specific user or a role, this is done in the file corresponding to the tests to be run.

# Designing Features

## Features

In order to describe the scenarios for each of Clarive's functionalities, we will use the same Gherkin language
previously described. Generally, this starts with the `.feature` file, describing the user story:

    Feature: User change password
        As a user
        In order to maintain application security
        I want to be able to change my password

Next up, the test preconditions are described. These preconditions are common to all scenarios described below:

    Background:
       Given "TestCommon" database
         And user "can_change_password" is logged in
         And user opens "change password" window

Lastly, we write the scenario using language as natural as possible, as the natural language will be 'translated' in the
`basic_steps.pl` file into code:

       Scenario: User can change password
         Given user fills "oldpass" with "<old_password>"
           And user fills "newpass" with "<new_password>"
           And user fills "pass-cfrm" with "<repeat_password>"
         When user confirms
         Then user can log in as "can_change_password" with "<repeat_password>"
        Examples:
           | old_password | new_password | repeat_password |
           | password     | new_password | new_password    |

We can see from this example that it is possible to use variables in order to use the same scenario, albeit with
different values, without having to re-write the scenario for every situation.

As a general rule, we will start by writing the correct test cases (*happy paths*), followed by exceptional test cases
or those that have to complete with errors.

### Good practices when writing Features

#### 1. Features have to test parts or functionalities of the tool

A feature represents a functionality of the software to be built, features requested by users, hence the name. For
example, “Perform a login” would be a feature.

#### 2. Use the clients' language

Gherkin is very similar to natural language, aiding communication between business, devs and QA.

#### 3. Organize features

A useful way of organizing scenarios is, for example, by the functionality being tested.

#### 4. Write scenarios to be as standalone as possible

Ideally, there should be no interconnection between Scenarios, and thus there should be independence between them, in
other words they should be as independent from each other and as standalone as possible.

#### 5. Avoid using logical operators in one step

Each step should do one thing. When a single step contains two actions separated using *and*, you probably need to
divide it into two separate *steps*. Having an action in every step increases potential for reusability. This is not
a general rule; one Step may contain two actions, although it is usually better to avoid them.

#### 6. Write a narrative

Narratives describe what a feature does or what it is about. Narratives are important for knowing first of all what this
feature is going to implement (and therefore, what is going to be tested). They also contain a short description of the
functionality in order to give other users reading them a rough idea of what it is about without reading the scenarios.

#### 7. Use the background consistently

If we use the same *steps* at the start of every scenario in a feature, ideally we should remove those steps from
scenarios and move them to the feature's background section. Backgrounds are run before each scenario. Be careful,
however, when putting Steps in the Background, since too many steps can become confusing and difficult to maintain.

# Designing basic\_steps

When designing `basic_steps`, as a general rule these should be ordered depending on the type of step, in other words,
Givens are defined first, followed by Whens, and last to be defined are Thens.

## Adding our own CSS classes

In order to perform tests, it is necessary to interact with the different CSS classes available in the tool. The team
may add the classes necessary for identifying an item, but should **always** follow naming conventions, whereby the
class should start with `ui-` and contain a name that represents the item in question.

All such changes made should go in a commit separately from test and feature design.
