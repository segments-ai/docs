# Cloud integrations

## AWS

### Granting cross-account access

If your data is stored in a private AWS S3 bucket, you can submit your image URLs in _virtual-hosted-style format_: `https://<bucket-name>.s3.<region>.amazonaws.com/<key>`.

We will then use the S3 API to access data from your S3 bucket, using AWS account ID `931508227573` (canonical ID `a2c85e730d80dcb51a2c0e1a8f852cf6dc8d6e04d9e00f49239c324de3c1e3e1`). We generate temporary [presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html) to serve the images from your S3 bucket in our frontend. These URLs expire after 24 hours.

This setup requires that you give the Segments.ai AWS account read-only access to the data in your bucket. You can do this by granting us [cross-account access](https://aws.amazon.com/premiumsupport/knowledge-center/cross-account-access-s3/) through setting an appropriate [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html):

1. In your AWS account, go to the S3 Management Console.
2. Go to your bucket.
3. Go to the **Permissions** tab.
4. In the **Bucket Policy** section, click the **Edit** button.
5. Paste the following bucket policy and save your changes. Don't forget to replace `YOUR_BUCKET_NAME` with the name of your bucket.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "segments-s3-access",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::931508227573:user/segmentsai-prod-user"
            },
            "Action": [
                "s3:GetObject"
            ],
            "Resource": "arn:aws:s3:::YOUR_BUCKET_NAME/*"
        }
    ]
}
```

{% hint style="info" %}
If you run into any issues when setting up this integration, please [contact us](https://segments.ai/contact).
{% endhint %}

### CORS configuration

You also need to configure [CORS](https://docs.aws.amazon.com/AmazonS3/latest/userguide/cors.html) for your S3 bucket:

1. In your AWS account, go to the S3 Management Console.
2. Go to your bucket.
3. Go to the **Permissions** tab.
4. In the **Cross-origin resource sharing (CORS)** section, click the **Edit** button.
5. Paste the following configuration and save your changes.

```
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "GET"
        ],
        "AllowedOrigins": [
            "https://*.segments.ai"
        ],
        "ExposeHeaders": []
    }
]
```

## Google Cloud

### Granting cross-account access

1. Please [contact us](https://segments.ai/contact) to request a Service Account Email ID for this GCP integration.
2. In your GCS account, go to your **GCS bucket permissions**.
3. Click **Add permissions** and paste the Service Account Email ID that we shared with you in the **New principals** field.
4. Select **Cloud Storage -> Storage Object Viewer** as the role, and press Save.
5. Configure **CORS** on your bucket as follows:
   1. Click the **Activate Cloud Shell** button (a terminal window icon) in the top-right corner
   2. In Cloud Shell, create a JSON file containing the CORS configuration by entering the command `echo '[{"origin":["https://*.`[`segments.ai`](http://segments.ai/)`"],"method":["GET"],"responseHeader":["*"]}]' > cors-config.json`
   3. Apply the CORS configuration to the bucket with the command `gsutil cors set cors-config.json gs://<bucket-name>`
6. Verify the CORS configuration with the command `gsutil cors get gs://<bucket-name>`
7. Please [share the name of your bucket with us](https://segments.ai/contact), so we can enable the integration on our side

Once this is set up, you can start using `gs://` URLs in your samples, pointing to files in your private bucket.

## Azure

### Granting cross-account access

1. Sign in to the [Azure Portal](https://portal.azure.com/).
2. In the search bar at the top, type **Microsoft Entra ID.**
3. Copy the **Tenant ID** on the **Overview** page and [share it with us](https://segments.ai/contact).
4. Install the **Segments.ai Blob Link Service app** into your tenant by running `az ad sp create --id d47021c7-05d1-44c3-a594-93c2c30c68fc` ([Azure docs](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/create-service-principal-cross-tenant?pivots=azure-cli)).
5. Grant the app access to your storage account:
   1. In the Azure Portal, go to the **Storage Account** you want to share.
   2. In the left menu, select **Access control (IAM)**.
   3. Click **+ Add → Add role assignment**.
   4. Choose **Storage Blob Data Reader** as the role (= read access only).
   5. Select **Assign access to → User, group, or service principal**.
   6. Find the **Enterprise application** you just created for the Segments.ai - Blob Link Service app.
   7. Save the assignment.

### CORS configuration

You also need to configure [CORS](https://learn.microsoft.com/en-us/cli/azure/storage/cors?view=azure-cli-latest) by running this Azure CLI command:

```
az storage cors add
--services b
--methods GET
--origins https://app.segments.ai https://webgpu.segments.ai
--max-age 3600
--account-name <yourStorageAccountName>
```

You can also [configure CORS via the Azure Portal](https://learn.microsoft.com/en-us/azure/container-apps/cors?tabs=arm\&pivots=azure-portal).
