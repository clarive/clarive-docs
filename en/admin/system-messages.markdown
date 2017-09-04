---
title: System Messages
index: 5000
icon: service-job-sms
---

System messages are system-wide notifications that are posted to all registered Clarive users.

They are useful for notifying of upcoming downtime, e.g. due to maintenance or publishing change-of-behaviour and
lifecycle enhancement notices to users.

### Messaging behaviour

The messaging campaign starts once the message is published.  Messages being read are kept track of and can be seen by
the message administrators in the *Read* column, which indicates how many unique users have seen the message.

Clicking on `Read` opens the list of users who have dissmissed the message. Since the message is actually bothersome,
because it limits the access to the menu bar on top, search and other functions, users are expected to dismiss messages
by closing them.

### ![](/static/images/icons/edit.svg) Creating a new message

Enter the `System Messages` admin option. The system messages window will open with a list of current and previous
messages.

Click on `Compose` to create a new message.

- **Title** - The message title shown in the upper bar. Keep it short, something like "New Release Tip" or "Maintenance
  scheduled".
- **Text** - The longer message shown in the upper bar. The title can actually be long, up to 130 characters is an
  acceptable title.
- **Expires** - When the message will stop being shown to users. Follow the format (1H - 1 hour, 1D - one day etc.).
- **Users** - Direct the message to only a given user. This can be used to quickly message a user who is logged in. Empty
  field means that all users will receive the message.
- **More Info** - *Optional*. A longer message body, with detailed content.  The text area accepts even images, where you
  can explain a new behaviour or phone numbers to call, etc.

Click on `Publish` to publish the message immediately.

### Testing a new message

To test a message before making it public, we recommend setting the username field to oneself, i.e.  the user who is
publishing the message.

If the message is deemed ready for public releases, simply clone the message and re-publish it to a larger audience.

### ![](/static/images/icons/delete.svg) Stop broadcasting messages

Simply `Delete` a message from the list.

### ![](/static/images/icons/copy.svg) Cloning an existing message

This allows for a previous message to be cloned, making it easier to create a new messaging campaign based on a previous
one.
