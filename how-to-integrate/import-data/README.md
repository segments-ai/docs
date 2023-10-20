# Import data

There are two ways to import the data you want to label:

1. Upload the data to Segments.ai's asset storage service via the web interface or Python SDK.
2. Keep the data in your own cloud bucket and submit the URLs to Segments.ai via the Python SDK.

## 1. Upload data to Segments.ai's asset storage service

{% hint style="warning" %}
The maximum file size for our asset storage service is 100MB.
{% endhint %}

### Via the web interface

Within a dataset, click the "Add samples" button or drag and drop files to the page. The uploaded assets (e.g. image or point cloud files) are stored in the Segments AWS S3 bucket. The asset URLs are public but unguessable, making them only accessible to dataset collaborators.&#x20;

### Via the Python SDK

See the [Python SDK reference](https://sdkdocs.segments.ai/en/latest/client.html#upload-an-asset-to-segments-s3-bucket).

## 2. Keep the data in your cloud bucket

If you want to keep the data in your own cloud bucket or on your own file server, you can use the [Python SDK to submit the URLs](https://sdkdocs.segments.ai/en/latest/client.html#create-a-sample) to Segments.ai. In this case, no data is copied to our own storage system, only a reference (URL) to the data is stored in our database. This can be done in three ways:

### **Public but unguessable URLs**

Keep the data in a cloud bucket whose content can be publicly accessed but not listed. You store the assets in this bucket with unguessable file names (containing a random uuid) such that they can only be accessed by third parties who you've shared the URLs with.

### **Customer-secured URLs**

Keep the data in a private cloud bucket or server, and generate proxied or pre-signed URLs on your end to retain full control of the access permissions. These URLs can have custom restrictions: expiry time, maximum number of accesses, IP whitelisting, rate limits, etc.

### **Cross-account access**

Keep the data in a private cloud bucket or server, and grant us cross-account access. In this case, we generate temporary pre-signed URLs whenever the images need to be displayed in the frontend. For setting this up, see [Cloud integrations](cloud-integration.md).
