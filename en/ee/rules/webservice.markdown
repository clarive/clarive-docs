---
title: Webservice Rules
icon: rule
index: 1020
---

Webservice rules are exposed through URLs that
can be called by other applications.

Webservice rules receive the web parameters such as the sub-path and and return
data that can be translated into different formats. The return format is up to
the caller to decide.

### Request Data

The request will arrive to the rule with the
following stash keys:

- `ws_params` - the `GET` or `POST` params as a hash/object.

- `ws_body` - the raw request body.

- `ws_headers` - the request header as a hash/object.
The headers sent depend on the user agent (a browser, cURL or any language web request library).
Header with keys may include `Content-Type`, `Accept-Language` and others.

- `ws_arguments` - an array with the URL path parts behind the URL, ie. for the
URL `https://clariveserver/rule/json/myrule/my/path` the stash variable
will hold `[ 'my', 'path']`.

- `ws_uploads` - the request uploaded file handler.

- `WSURL` - the URI called by the requester, in the following format `schema://[authority][path]`.

- `username` - the username of the authenticated user.

For all these, the `ws_params` is the most useful data. To access a certain parameter
use the following variable construction:

```bash
    ${ws_params.myvar}
```

### Return Data Formats

Possible return data formats from webservice rules are:

- JSON
- YAML
- XML
- Raw - simple plain text or binary data returned by a Rule

The caller sets the desired format in the calling URL, following the webservice
URL format:

```bash
    http(s)://clariveserver/rule/[json|yaml|xml|raw]/[rule-id]
```

### Webservice Rule Authentication

Webservice endpoints can be either authenticated or public.

Public endpoints can be accessed by anyone. Never implement public webservices
that run sensitive operations. Public webservices may be useful for reporting
public data as JSON, for instance.

The authentication method is through an **api-key**. API keys are managed on a
per User basis.

We recommend creating specific Users, setting their permissions, then capturing
the api-key for that User to be used in the URL.
