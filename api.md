# API

The API is available at **https://api.segments.ai/**. 

To authenticate, add an API key in the header of each request:

```bash
curl -H "Authorization: APIKey YOUR_API_KEY"
```

An API key can be created on your [user account page](https://segments.ai/account).

## Datasets

### List datasets

```bash
GET /users/:owner/datasets
```

To get all datasets of the currently logged in users, you can use this shortcut:

```bash
GET /user/datasets
```

{% hint style="info" %}
Note that this will only return datasets which are public, and datasets which are private but where the logged in user is a collaborator.
{% endhint %}

#### Response

{% code title="Status: 200 OK" %}
```bash
[
    {
        "name": "cats",
        "description": "A dataset of cat images.",
        "data_type": "IMAGE",
        "category": "other",
        "public": false,
        "owner": {
            "username": "bert",
            "email": "bert@segments.ai",
            "created_at": "2020-05-11T14:00:53.763278Z"
        },
        "created_at": "2020-04-10T20:09:31Z",
        "collaborators_count": 0,
        "samples_count": 94        
    }
]
```
{% endcode %}

### Get a dataset

```bash
GET /datasets/:owner/:dataset
```

#### Response

{% code title="Status: 200 OK" %}
```bash
{
    "name": "cats",
    "description": "A dataset of cat images.",
    "category": "other",
    "public": false,
    "owner": {
        "username": "bert",
        "created_at": "2020-05-11T14:00:53.763278Z"
    },
    "created_at": "2020-07-20T14:59:36.242218Z",
    "collaborators_count": 0,
    "samples_count": 94,
    "task_type": "segmentation-bitmap",
    "task_attributes": {
        "format_version": "0.1",
        "categories": [
            {
                "name": "cat",
                "id": 0
            },
            {
                "name": "dog",
                "id": 1
            }
        ]
    },
    "labelsets": [
        {
            "name": "ground-truth",
            "description": "Ground truth labels.",
        },
        {
            "name": "predictions",
            "description": "My model predictions.",
        },
    ]
}
```
{% endcode %}

### Create a dataset

```bash
POST /user/datasets
```

#### Input

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>name</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left"><b>Required. </b>The name of the dataset.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>description</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">The description of the dataset.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>task_type</code>
      </td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p>The task type of the dataset. Can be one of:</p>
        <ul>
          <li><code>segmentation-bitmap</code>: Semantic, panoptic and instance segmentation.</li>
          <li><code>vector</code>: Polygons, polylines, bounding boxes, points.</li>
          <li><code>bboxes</code>: Bounding boxes only.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>task_attributes</code>
      </td>
      <td style="text-align:left">dict</td>
      <td style="text-align:left">The task attributes. See <a href="configure-label-editor.md">Configuring the label editor</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>category</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">Category of the data.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>public</code>
      </td>
      <td style="text-align:left"><code>boolean</code>
      </td>
      <td style="text-align:left">
        <p>Sets the visibility of a dataset. Can be one of:</p>
        <ul>
          <li><code>true</code> - Anyone can see the dataset.</li>
          <li><code>false</code> - Only the owner and collaborators can view the dataset.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>readme</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">The readme of the dataset, displayed on the overview tab.</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
{
  "name": "cats",
  "description": "A dataset of cat images."
}
```

#### Response

{% code title="Status: 201 Created" %}
```bash
{
    "name": "cats",
    "description": "A dataset of cat images.",
    "category": "other",
    "public": false,
    "owner": {
        "username": "bert",
        "email": "bert@segments.ai",
        "created_at": "2020-05-11T14:00:53.763278Z"
    },
    "created_at": "2020-07-20T14:59:36.242218Z",
    "collaborators_count": 0,
    "samples_count": 94
}
```
{% endcode %}

### Update a dataset

```bash
PATCH /datasets/:owner/:dataset
```

Same fields as previous.

### Delete a dataset

```bash
DELETE /datasets/:owner/:dataset
```

### Add a collaborator to a dataset

```bash
POST /datasets/:owner/:dataset/collaborators
```

#### Input

| Name | Type | Description |
| :--- | :--- | :--- |
| `user` | `string` | **Required.** The username of the collaborator to be added. |
| `role` | `string` | The role of the collaborator. Can be one of: `labeler`, `reviewer`, `admin` |

#### Example

```bash
{
  "user": "jane",
  "role": "reviewer"
}
```

#### Response

{% code title="Status: 201 Created" %}
```bash
{
  "user": "jane",
  "role": "reviewer"
}
```
{% endcode %}

## Samples

### List samples

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
      },
    "metadata": {},
    "priority": 0,
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
  },
  "metadata": {}
  "priority": 0,
  "created_at": "2020-04-10T20:09:31Z"
  "created_by": "jane",
  "dataset": "jane/cats"
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
| `metadata` | `object` | User-defined metadata. |
| `priority` | `float` | Priority in the labeling queue. Samples with higher values will be labeled first. Default is 0. |

#### Example

```bash
{
  "name": "flowers.png",
  "attributes": {
    "image": {
      "url": "https://example.com/image.png"
    }
  },
  "metadata": {
    "city": "London",
    "weather": "cloudy",
    "robot_id": 3
  },
  "priority": 10
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
  },
  "metadata": {
    "city": "London",
    "weather": "cloudy",
    "robot_id": 3
  },
  "priority": 10,
  "created_at": "2011-04-10T20:09:31Z"
  "created_by": "jane"
}
```
{% endcode %}

### Update a sample

```bash
PATCH /samples/:sample_uuid
```

Same fields as previous.

### Delete a sample

```bash
DELETE /samples/:sample_uuid
```

## Labels

### Get a label

```bash
GET /labels/:sample_uuid/:labelset
```

#### Response

{% code title="Status: 200 OK" %}
```bash
{
  "label_type": "segmentation-bitmap",
  "label_status": "LABELED",
  "attributes": {
    "format_version": "0.1",
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
  "created_at": "2020-04-10T20:09:31Z",
  "created_by": "jane",
}
```
{% endcode %}

### Create or update a label

```bash
PUT /labels/:sample_uuid/:labelset
```

#### Input

<table>
  <thead>
    <tr>
      <th style="text-align:left">Name</th>
      <th style="text-align:left">Type</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>attributes</code>
      </td>
      <td style="text-align:left"><code>object</code>
      </td>
      <td style="text-align:left">Label data. Format depends on the label type, see <a href="label-types.md">label formats</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>label_status</code>
      </td>
      <td style="text-align:left"><code>string</code>
      </td>
      <td style="text-align:left">
        <p>Status of the label.</p>
        <p></p>
        <p>Can be one of: <code>LABELED</code>, <code>REVIEWED</code>, <code>REJECTED</code>, <code>PRELABELED</code>, <code>SKIPPED</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>score</code>
      </td>
      <td style="text-align:left"><code>float</code>
      </td>
      <td style="text-align:left">Prediction score.</td>
    </tr>
  </tbody>
</table>

#### Example

```bash
{
  "attributes": {
    "format_version": "0.1",
    "annotations": [
      {
        "id": 1,
        "category_id": 0,
      }
    ],
    "segmentation_bitmap": {
      "url": "https://example.com/label.png"
    }
  },
  "label_status": "PRELABELED",
  "score": 0.9254
}
```

#### Response

{% code title="Status: 201 Created" %}
```bash
{
  "attributes": {
    "format_version": "0.1",
    "annotations": [
      {
        "id": 1,
        "category_id": 0,
      }
    ],
    "segmentation_bitmap": {
      "url": "https://example.com/label.png"
    }
  },
  "label_status": "PRELABELED",
  "created_at": "2011-04-10T20:09:31Z"
}
```
{% endcode %}

### Delete a label

```bash
DELETE /labels/:sample_uuid/:labelset
```

## Releases

### List releases

```bash
GET /datasets/:owner/:dataset/releases
```

#### Response

{% code title="Status: 200 OK" %}
```bash
[
  {
    "name": "v0.1",
    "description": "My first release.",
    "attributes": {
      "url": "https://segmentsai-prod.s3.eu-west-2.amazonaws.com/releases/f0b0a34b-93ca-41a3-06ee-96ce6436dd41.json"
    },
    "status": "SUCCEEDED",
    "created_at": "2020-07-20T14:59:36.242218Z"
  }
]
```
{% endcode %}

### Get a release

```bash
GET /datasets/:owner/:dataset/releases/:release_name
```

#### Response

{% code title="Status: 200 OK" %}
```bash
{
  "name": "v0.1",
  "description": "My first release.",
  "attributes": {
    "url": "https://segmentsai-prod.s3.eu-west-2.amazonaws.com/releases/f0b0a34b-93ca-41a3-06ee-96ce6436dd41.json"
  },
  "status": "SUCCEEDED",
  "created_at": "2020-07-20T14:59:36.242218Z"
}
```
{% endcode %}

### Create a release

```bash
POST /datasets/:owner/:dataset/releases
```

#### Input

| Name | Type | Description |
| :--- | :--- | :--- |
| `name` | `string` | **Required.** The name of the release. |
| `description` | `string` | The description of the release. |

#### Example

```bash
{
  "name": "v0.1",
  "description": "My first release."
}
```

#### Response

{% code title="Status: 201 Created" %}
```bash
{
  "name": "v0.1",
  "description": "My first release.",
  "status": "PENDING",
  "created_at": "2020-07-20T14:59:36.242218Z"
}
```
{% endcode %}

### Delete a release

```bash
DELETE /datasets/:owner/:dataset/releases/:release_name
```

## 

