---
description: >-
  Listen for events on your account so your integration can automatically
  trigger reactions.
---

# Webhooks

Webhooks are automated messages sent to your server when something happens. You can use webhooks to subscribe to certain events on your account and automatically trigger reactions.

To enable webhooks for the datasets under your account, go to [your account page](https://segments.ai/account) and click the "Enable" button in the webhooks section. Then click the "Manage webhooks" button to add endpoints, subscribe to events, view and replay webhooks.

Every webhook is signed with a unique key for increased security. Please refer to [these docs](https://docs.svix.com/receiving/verifying-payloads/how) to verify and validate your incoming webhooks.

You can currently subscribe to following events:

| Event type | Description |
| :--- | :--- |
| `dataset.created` | Occurs whenever a dataset is created. |
| `dataset.updated` | Occurs whenever a dataset property has changed. |
| `dataset.deleted` | Occurs whenever a dataset is deleted. |
| `sample.created` | Occurs whenever a sample is created. |
| `sample.updated` | Occurs whenever a sample property has changed. |
| `sample.deleted` | Occurs whenever a sample is deleted. |
| `label.updated` | Occurs whenever a label property has changed. |
| `label.deleted` | Occurs whenever a label is deleted. |
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

## Setting up a Slack integration with webhooks

This is a guided tutorial on how to set up a Slack integration using webhooks with [Segments.ai](http://segments.ai/). For more information, please refer to [Slack's instructions](https://api.slack.com/messaging/webhooks).

### Create a Slack app, enable incoming webhooks and create an endpoint URL in Slack

1. Create a Slack app, enable incoming webhooks and create an endpoint URL in Slack
2. You'll be redirected to its settings page. From here, select the Incoming Webhooks feature and toggle on the Activate Incoming Webhooks.
3. Some extra options will now appear. In the bottom of the page, click the Add New Webhook to Workspace button and choose a channel. Make sure the channel is a [public channel](https://slack.com/intl/en-be/help/articles/360017938993-What-is-a-channel) within your Slack workspace.
4. You'll be sent back to your app settings, and you should now see a new Webhook URL entry with an endpoint URL resembling something like `https://hooks.slack.com/services/T00000000/B00000000/XXXXXXXXXXXXXXXXXXXXXXXX`

{% hint style="warning" %}
You've now created an endpoint URL for the incoming webhook, specific to a single user and a single channel.
{% endhint %}

### Configure your webhooks in Segments.ai using the Slack endpoint URL

1. Go to your [Segments.ai account page](https://segments.ai/account/) and click the "Enable" button in the webhooks section.
2. Click the green "Manage webhooks" button and you'll be taken to the webhook configuration page.
3. Add an endpoint and provide the following items in the configuration window:
   * The endpoint URL that you just created in the Slack settings
   * An optional version number and description
   * Which events to send notifications about to the Slack channel

The webhook will then be created.

{% hint style="info" %}
You will start to receive notifications, but only for those events within datasets of which you're an owner.
{% endhint %}

