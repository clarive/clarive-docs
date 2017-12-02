---
title: Using Clarive APIs
index: 4000
---

The Clarive Application Programming Interface or API does not offer out-of-the
box URL endpoints. You have to expose them first. This means creating
webservice rules, then exposing the endpoint to your external application.

Webservice rules can be exposed as either REST or SOAP endpoints, which
improves connectivity and centralizes the execution of automation logic.

The Clarive API's powerful primitives are available within the Rule, using
operations or working with JavaScript code directly.

Therefore, the Clarive recommended way to implement calls to our API is:

1) Write a webservice rule that exposes the endpoint URL.

2) Call that URL externally, setting the return data format in the URL.

#### Why we don't offer just a simple REST API?

Exposing REST APIs means you can automate logical sequences from external
tools, programming languages or scripts.

We firmly believe creating scripts outside of the tool is problematic,
especially since Clarive is an automation tool with advanced monitoring,
logging, concurrency control and event handling built in. Also, we include
testing and dry-run modes that can help you debug your delivery automation
logic in one go for when you take automation logic outside of Clarive into
other tools.

For example, you could write a script that creates a Topic, fills out some
data, then promotes the Topic to the next status.

Alternatively, the same can be done in a webservice rule, you write a
webservice rule that first carries this out, and then calls that endpoint with
something like *curl* (the `curl` commmand, which can be used to call REST
URLs).

#### Building Plugins

If you are an independent vendor or programmer who wants to integrate your tool
with Clarive by writing a plugin, you have to write the part of your plugin
that runs under Clarive, then have it installed under the
`CLARIVE_BASE/plugins` directory.

### The Clarive API

Here are a list of the main primitives of the Clarive API, exposed through the Rule operations:

- Create, update, delete, list topics.
- Create, update, delete, list Resources.
- Deployment and job management.
- Notifications.
- Event management.
- Semaphores.
- Provisioning.
- Impact analysis.
- MongoDB operations.

Please refer to the [Introduction](/devel/intro) for a detailed explanation on what the Clarive API offers.

#### Return Data Formats

Possible return data formats from webservice rules are:

- JSON
- YAML
- XML
- Raw - simple plain text or binary data returned by a Rule

Simply set the desired format in the URL, following the webservice URL format:

    http(s)://clariveserver/rule/[json|yaml|xml|raw]/[rule-id]

### Authentication

Webservice endpoints can be either authenticated or public.

Public endpoints can be accessed by anyone. Never implement public webservices
that run sensitive operations. Public webservices may be useful for reporting
public data as JSON, for instance.

The authentication method is through an **api-key**. API keys are managed on a
per User basis.

We recommend creating specific Users, setting their permissions, then capturing
the api-key for that User to be used in the URL.
