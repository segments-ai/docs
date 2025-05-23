---
description: >-
  On the Segments.ai web platform you can create datasets, upload samples,
  create releases and download labels. All of these - and more - can also be
  done programmatically with the Python SDK.
---

# Python SDK quickstart

{% hint style="info" %}
This tutorial walks you through the most common Python SDK functions. The complete list of functions is documented in detail in the [Python SDK reference](https://sdkdocs.segments.ai/).
{% endhint %}

First install the Segments.ai Python SDK using pip:

```
pip install --upgrade segments-ai
```

Import the necessary packages, and initialize the Segments client using your API key:&#x20;

```python
from segments import SegmentsClient
import json

# You can find your api key at https://segments.ai/account
api_key = "YOUR_API_KEY_HERE"

client = SegmentsClient(api_key)
```

## Create a new dataset

Let's create a new image segmentation dataset programmatically using [`client.add_dataset()`](https://sdkdocs.segments.ai/en/latest/client.html#create-a-dataset). Note that this dataset will be created under the user account corresponding to the API key.

{% hint style="info" %}
The format of the `task_attributes` field is documented [here](../reference/categories-and-attributes.md).
{% endhint %}

```python
name = "pets"
description = "A dataset with images of cats and dogs."
task_type = "segmentation-bitmap"

task_attributes = {
 "format_version": "0.1",
 "categories": [
  {
   "name": "cat",
   "id": 1
  },
  {
   "name": "dog",
   "id": 2
  },
  {
   "name": "other",
   "id": 3
  }
 ]
}

dataset = client.add_dataset(name, description, task_type, task_attributes)
print(dataset)
```

## Add samples to a dataset

Now let's upload some images to this dataset using [`dataset.add_sample()`](https://sdkdocs.segments.ai/en/latest/client.html#create-a-sample).

```python
dataset_identifier = 'jane/pets' # a dataset is always referred to as user/dataset.

images = [
    {
        'name': 'Bombay_220.jpg', 
        'url': 'https://segmentsai-prod.s3.eu-west-2.amazonaws.com/assets/jane/a13358ef-a1ae-443c-8ea1-5f61dd9cdc26.jpg'
    },
    {
        'name': 'shiba_inu_178.jpg', 
        'url': 'https://segmentsai-prod.s3.eu-west-2.amazonaws.com/assets/jane/4f47973f-5568-47f1-8a7d-44bfeb6f0f76.jpg'
    },
    {
        'name': 'havanese_196.jpg', 
        'url': 'https://segmentsai-prod.s3.eu-west-2.amazonaws.com/assets/jane/2a6b3cd9-0688-422b-b555-8730d0813e1b.jpg'
    }
]

dataset = client.get_dataset(dataset_identifier)
for image in images:    
    name = image['name']
    attributes = {
        'image': {
          'url': image['url'] 
        }
    }
    sample = dataset.add_sample(name, attributes)
    print(sample)
```

{% hint style="warning" %}
If the image file is on your local computer, you should first upload it to our asset storage service (using [`upload_asset()`](https://sdkdocs.segments.ai/en/latest/client.html#upload-an-asset-to-segments-s3-bucket)) or to another cloud storage service.
{% endhint %}

We can verify that the dataset now contains 3 images using [`dataset.get_samples()`](https://sdkdocs.segments.ai/en/latest/client.html#list-samples).

```python
dataset_identifier = 'jane/pets'
dataset = client.get_dataset(dataset_identifier)

samples = dataset.get_samples()
print(samples)
```

Now switch to the Segments.ai web platform and label the three images you just uploaded by pressing the "Start labeling" button.

## Get the label of a sample

Once you've labeled some samples, you can programmatically retrieve their labels using [`sample.get_label()`](https://sdkdocs.segments.ai/en/latest/client.html#get-a-label).

```python
dataset_identifier = 'jane/pets'
sample = client.get_dataset(dataset_identifier).get_samples()[0]

label = sample.get_label(labelset='ground-truth')
print(label)
```

## Optional: visualize the instance and semantic labels

When working with image segmentation datasets, you'll probably want to visualize the image and label at this point. The `segments.utils` module offers some helper functions for that:

```python
import numpy as np
import matplotlib.pyplot as plt
from segments.utils import load_image_from_url, load_label_bitmap_from_url, get_semantic_bitmap

# Load the labels as numpy arrays
image = load_image_from_url(sample.attributes.image.url)
instance_bitmap = load_label_bitmap_from_url(label.attributes.segmentation_bitmap.url)
semantic_bitmap = get_semantic_bitmap(instance_bitmap, label.attributes.annotations)

# Visualize
plt.imshow(image)
plt.title('Image')
plt.show()

plt.imshow(instance_bitmap)
plt.title(f'Instance bitmap. Values represent instance ids: {np.unique(instance_bitmap)}')
plt.show()

plt.imshow(semantic_bitmap)
plt.title(f'Semantic bitmap. Values represent category ids: {np.unique(semantic_bitmap)}')
plt.show()
```

## What's next?

The Python SDK offers many more functions besides the ones that were shown here. Have a look at the [reference](https://sdkdocs.segments.ai/en/latest/client.html) for the full list.

The Python SDK can also be used to upload labels into Segments.ai. This is particularly useful for setting up [model-assisted labeling](model-assisted-labeling.md) workflows, where you verify and correct model predictions instead of labeling from scratch.
