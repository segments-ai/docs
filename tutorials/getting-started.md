---
description: >-
  This tutorial shows how you can create a dataset, upload some images in it,
  label and review them, and finally create a dataset release to export your
  data.
---

# Getting started

{% hint style="info" %}
If you want to know how to interact programmatically with Segments.ai, follow the [Python SDK quickstart](python-sdk-quickstart.md) instead.
{% endhint %}

First, make sure you've [created an account](https://segments.ai/join) and are logged in. Clicking on the Segments.ai logo in the upper left corner, takes you to your home screen:

![On the home screen you see a list of all your own datasets, and the datasets of others in which you're a collaborator.](<../.gitbook/assets/image (25) (1).png>)

## Create a new dataset

From the home screen, click the "New dataset" button. Choose a dataset name and description, set the visibility, and choose a category. Then click "Next".

Choose "Segmentation (bitmap)" for the task type in this tutorial. We will be labeling a dataset of pets in this tutorial, so we add three object categories: cat, dog and other.&#x20;

Finally, click "Create dataset".

![](<../.gitbook/assets/image (14).png>)

## Upload images

Now that you've created a new dataset, let's add some images to it. In your dataset, go to the Samples tab and click the "Add Samples" button.

{% hint style="info" %}
A sample can be an image, video or 3D pointcloud. In this tutorial we're working with images.
{% endhint %}

![](<../.gitbook/assets/image (24) (1) (1).png>)

Select a few images and upload them. The images appear as thumbnails in the Samples tab.

![](<../.gitbook/assets/image (18).png>)

## Label and review

Press the "Start labeling" button. This brings you into the labeling workflow, where you will be presented with unlabeled images until the labeling queue is empty.&#x20;

Label all objects in the image and press "Submit", until all images are labeled. More details on effectively using the segmentation interface can be found [here](../guides/use-the-labeling-interfaces/image-segmentation-interface.md).

![](<../.gitbook/assets/image (7).png>)

When done labeling, press the little cross icon in the top right corner to exit the labeling interface.

Optionally, press the "Start reviewing" button. This brings you into the reviewing workflow, where you can accept or reject labeled images. Rejected images go back to the labeling queue for correction.

{% hint style="info" %}
Instead of using the "Start labeling" and "Start reviewing" buttons, you can also open and edit any image directly by clicking its thumbnail. Note that in this case, the image is not prevented from being edited by someone else at the same time.
{% endhint %}

## Export data

Go to the Releases tab. Here you can create a snapshot of your dataset with a download link to the finished labels.

Press the "Create a new release button" and choose a name and description for the release. Creating the release may take a few seconds.

![](<../.gitbook/assets/image (15).png>)

For more details on exporting data to different formats, see the [Export data](../export.md) section.
