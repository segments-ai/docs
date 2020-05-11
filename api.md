# API

The API is available at **https://api.segments.ai/**. 

To authenticate, add an API key in the header of each request:

```bash
curl -H "Authorization: APIKey YOUR_API_KEY"
```

An API key can be created on your user account page.

## Samples

### List samples of a dataset

```bash
GET /datasets/:owner/:dataset/samples
```

#### Parameters

| Name | Type | Description |
| :--- | :--- | :--- |
| `task` | `string` | Indicates the ... |

#### Response

{% code title="Status: 200 OK" %}
```bash
[
  {
    "uuid": "10130ecd-790e-463d-86ce-747f5c545c77",
    "name": "image.png"
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
}
```
{% endcode %}

### Create a sample

```bash
POST /samples
```

#### Input

| Name | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | **Required.** The name of the sample. |
|  |  |  |

#### Example

```bash
{
  "name": "myimage.png"
}
```

#### Response

{% code title="Status: 201 Created" %}
```bash
{
  "uuid": "10130ecd-790e-463d-86ce-747f5c545c77",
  "name": "myimage.png",
  "created_at": "2011-04-10T20:09:31Z",
}
```
{% endcode %}

## Labels

### Get a label

### Create a label

### Update a label



