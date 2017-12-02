---
title: API Key
index: 5000
icon: lock
---

An application programming interface key (API key) is a code passed in by external commands calling Clarive API
(application programming interface) to identify the calling user.

API keys are an alternative to using login credentials. They simply identify the user without having to send the
password.

!!! warning
    API keys are sensitive information. Store them with care. If stolen, an API key can give access to the data your Clarive
    user is entitled to view.

### Usage

*API keys* can be used in two forms:

- As a query setting calling a Clarive URL.
- As a user password alternative.

### Global API Key Access Setup

API keys cannot be used to log into the Clarive web interface or access any URL, except when the system configuration
option `api_key_authentication` is set to a true value.

    api_key_authentication: 1


### Error messages

!!! error "api-key authentication is not enabled for this url"
    This error message indicates that the URL accessed is not allowed for API keys. Either write a [webservice
    rule](/concepts/webservice) or enable global API key access.
