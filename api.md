# API

The API is available at **https://api.segments.ai/**. 

To authenticate, add an API key in the header of each request:

```bash
curl -H "Authorization: APIKey YOUR_API_KEY"
```

An API key can be created on your [user account page](https://segments.ai/account).

## Samples

### Get all samples in a dataset

```bash
GET /datasets/:owner/:dataset/samples
```

#### Response

{% code title="Status: 200 OK" %}
```bash
[
  {
    "uuid": "10130ecd-790e-463d-86ce-747f5c545c77",
    "name": "image.png"
    "data_type": "IMAGE",
    "attributes": {
        "image": {"url": "https://example.com/image.png"}
      }
    "created_at": "2011-04-10T20:09:31Z"
    "created_by": "jane"
  }
]
```
{% endcode %}

### Get a sample

```bash
GET /samples/:sample_uuid
```

#### Response

{% code title="Status: 200 OK" %}
```bash
{
  "uuid": "10130ecd-790e-463d-86ce-747f5c545c77",
  "name": "image.png"
  "data_type": "IMAGE",
  "attributes": {
    "image": {"url": "https://example.com/image.png"}
  }
  "created_at": "2011-04-10T20:09:31Z"
  "created_by": "jane"
}
```
{% endcode %}

### Create a sample

```bash
POST /datasets/:owner/:dataset/samples
```

#### Input

| Name | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | **Required.** The name of the sample. |
| `attributes` | `object` | Sample data. |

#### Example

```bash
{
  "name": "flowers.png",
  "attributes": {
    "image": {
      "url": "https://example.com/image.png"
    }
  }
}
```

#### Response

{% code title="Status: 201 Created" %}
```bash
{
  "uuid": "10130ecd-790e-463d-86ce-747f5c545c77",
  "name": "image.png"
  "data_type": "IMAGE",
  "attributes": {
    "image": {
      "url": "https://example.com/image.png"
    }
  }
  "created_at": "2011-04-10T20:09:31Z"
  "created_by": "jane"
}
```
{% endcode %}

## Labels

### Get a label

```bash
GET /labels/:sample_uuid/:task_name
```

#### Response

{% code title="Status: 200 OK" %}
```bash
{
  "label_type": "segmentation-bitmap",
  "label_status": "LABELED",
  "attributes": {
    "annotations": [
      {
        "id": 1, 
        "category_id": 0
      }
    ],
    "segmentation_bitmap": {
      "url": "https://segmentsai-staging.s3.eu-west-2.amazonaws.com/assets/davy/ddf55e99-1a6f-42d2-83e9-8657de3259a1.png"
    }
  },
  "created_at": "2011-04-10T20:09:31Z",
  "created_by": "jane"
}
```
{% endcode %}

