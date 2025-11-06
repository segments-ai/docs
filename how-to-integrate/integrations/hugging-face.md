---
hidden: true
---

# Hugging Face

[Hugging Face (🤗) Datasets](https://huggingface.co/docs/datasets/index) is a library for accessing and sharing machine learning datasets. It features powerful data processing methods to quickly get your dataset ready for training deep learning models.

## Export

You can export a Segments dataset release as a 🤗 Dataset using the `release2dataset` function in the Python SDK:

```python
from segments import SegmentsClient
from segments.huggingface import release2dataset

# Get a specific dataset release
client = SegmentsClient("YOUR_API_KEY")
release = client.get_release("jane/flowers", "v0.1")

# Convert it to a 🤗 Dataset
hf_dataset = release2dataset(release)
```

The returned object is a [🤗 Dataset object](https://huggingface.co/docs/datasets/package_reference/main_classes#datasets.Dataset). The columns of the exported dataset depend on the task type of the dataset, and closely follow our documented sample and label formats. The columns can be inspected as follows:

```python
>>> dataset.features

{
  'name': Value(dtype='string', id=None),
  'uuid': Value(dtype='string', id=None),
  'status': Value(dtype='string', id=None),
  'image': Image(decode=True, id=None),
  'label.annotations': [{'id': Value(dtype='int32', id=None), 'category_id': Value(dtype='int32', id=None)}],
  'label.segmentation_bitmap': Image(decode=True, id=None)
}
```

The [🤗 Dataset documentation](https://huggingface.co/docs/datasets/index) explains how you can modify the structure and contents of the exported dataset in all kinds of ways:

* Reorder the rows
* Rename and remove columns
* Apply a processing function to each row in the dataset
* Use as a PyTorch or TensorFlow dataset

## Publish to the Hugging Face Hub

You can also easily publish your dataset to the [Hugging Face Hub](https://huggingface.co/datasets):

```python
hf_dataset.push_to_hub("jane/flowers") # This is the name of a HF user/dataset
```

## Train models on your dataset

[This tutorial](https://huggingface.co/blog/fine-tune-segformer) shows how you can fine-tune a semantic segmentation model on a custom dataset exported from Segments. The process is similar for other task types.
