---
title: Creating and Updating Topics
index: 550
---

You can create and modify topics within your rulebooks.

## Create a topic

You must send at least the title, category and initial status for your topic:

```yaml
do:
   - mid = create_topic:
          category: Enhancement
          data:
            description: |
                 Just a short description
          status: New
          title: My topic title
```

The `create_topic` op will return the `mid` (id) of the new topic.

## Modify a topic

To modify a topic, you need at least the `mid` of the topic you want to modify.

```yaml
do:
    - update_topic:
         mid: ${mid}
         data:
            title: 'Changed it just now'

```

Depending on your context, the `mid` may be available in the context object.
For instance, if your rule is hooked to a `topic_modify` event:

```yaml
topic_modify:
    - topic =: "{{ ctx.topic() }}"
    - update_topic:
         mid: ${topic.mid}
         data:
            title: 'Changed it just now'

```

## Change the Topic Status

You can promote/demote a topic from one status to another with the
`change_status` op.

The `to` status can only be one, and is required.

```yaml
topic_modify:
    - topic =: "{{ ctx.topic() }}"
    - change_status:
        mid: ${topic.mid}
        to: Fixed
```

The `change_status` op can also change multiple topics at once and filter by
several `from` statuses.

```yaml
do:
    - change_status:
        mid: [ '123', '456' ],
        to: Fixed
```

You can also filter the `from` status, so that you guarantee only topics that
actually are in the `from` list have their statuses changed to the `to` status.

```yaml
do:
    - change_status:
        mid:
            - 123
            - 456
        from:
           - 'To Do'
           - 'In Progress'
        to: Fixed
```

## Permissions

The above ops will __always__ use the current user executing the
rulebook.

- For a pipeline job, it will be the user that created the job.

- For an event, the user that triggered the event.

- For a webhook call, the user authenticated into Clarive
  that called the webhook.

If the user does not have permissions to the topic project or
the topic category in question, a permissions error will be shown.
