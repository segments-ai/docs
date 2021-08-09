---
description: >-
  Listen for events on your account so your integration can automatically
  trigger reactions.
---

# Webhooks

To enable webhooks, go to [your account page](https://segments.ai/account) and click the "Enable" button in the webhooks section. Then click the "Manage webhooks" button to add endpoints, subscribe to events, view and replay webhooks.

Every webhook is signed with a unique key for increased security. Please refer to [these docs](https://docs.svix.com/receiving/verifying-payloads/how) to verify and validate your incoming webhooks.

You can currently subscribe to following events:

| Event type | Description |
| :--- | :--- |
| `dataset.created` | Occurs whenever a dataset is created. |
| `dataset.updated` | Occurs whenever a dataset property has changed. |
| `sample.created` | Occurs whenever a sample is created. |
| `sample.updated` | Occurs whenever a sample property has changed. |
| `label.updated` | Occurs whenever a label property has changed. |
| `issue.created` | Occurs whenever an issue is created. |
| `issue.updated` | Occurs whenever an issue has received a reply or a property has changed. |

The webhook payload looks as follows:

```javascript
{
  "event_type": "sample.created",
  "created_at": "2021-08-09T14:40:19.987691+00:00",
  "api_version": "2021-08-01",
  "dataset": "jane/flowers",
  "object": { ... }, // The dataset, sample, label or issue that was created or updated.
  "text": "Sample rose.png created in dataset jane/flowers." // Text summary, useful for Slack integration.
}
```

### Setting up a Slack integration

Follow [these instructions](https://api.slack.com/messaging/webhooks) to set up a Slack integration using webhooks.

