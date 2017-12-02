---
title: Webhook Rules
index: 2200
---

Webhook rules is a powerful tool for enabling access from the outside world to
your DevOps toolchain. With webhook rules one can write ad-hoc application
interfaces to Clarive, as well as custom web pages.

Webhook rules can be accessed through an exposed URL in Clarive. When a user or
program calls the URL, the rule logic will run just like with any other event.

To enable a webhook rule, just upload a `.clarive.yml` rulebook to a Git
repository with an event that starts with a forward slash `/`.

```yaml
name: my webhooks

/hello_world:
   - echo: "requested param={{ ctx.request('params') }}"
```

If the above rulebook is in `MyProject/MyRepo` under Clarive, the following
URL will be instanteneously exposed (the user needs to be logged in, ie from a browser):

    https://myclariveserver/rules/json/MyProject/MyRepo/hello_world

Calling the URL (with cURL for instance) will execute the `echo` op in the
`/hello_world` event webhook.

## Request Data

To get the request data, the following contexts are enabled:

Context                      |  Contents
-----------------------------|------------------------------------------------------
ctx.request('params')        | The URL query-string or form params in a hash
ctx.request('args')          | Array with each of the `/path` components of the URL
ctx.request('body')          | The full request body as a string
ctx.request('headers')       | HTTP request headers
ctx.request('upload')        | Uploaded files
ctx.user()                   | The user id who made the (authenticated) request

## Response data

Any response data should be sent using the `web_response:` op.

Valid `web_response` params:

        for my $meth ( qw(body cookies status redirect location write content_type headers header) ) {

Argument                     |  Contents
-----------------------------|------------------------------------------------------
body                         | The response body
cookies                      | A hash with the cookies to be set in the browser/client
status                       | The HTTP status
redirect                     | HTTP redirect
location                     | HTTP location string
content_type                 | Content-type string
headers                      | Response headers

## Authentication

Calls to webhook rulebooks need to be authenticated by default.

That means the user calling the rulebook needs to be logged in or
put an api_key as an argument to the rulebook call.

The permissions of the rulebook will be bound to the user calling the
rulebook, and never the owner that created the rule.

To use an api key, head over to the user menu, Preferences on the top right of the
Clarive UI, and Generate API Key (if never done before).

Copy the api_key and use it in the client that will call the rulebook:

    curl https://clariveserver/rule/json/MyProject/MyRepo/hello_world?api_key=9837492dac873473443489adcc8787
