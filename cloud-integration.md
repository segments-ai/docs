# Cloud integration

## AWS

### Granting cross-account access

If your data is stored in a private AWS S3 bucket, you can submit images as S3 protocol URIs. For example, instead of `https://s3-us-west-1.amazonaws.com/bucket/image001.png` you would submit `s3://bucket/image001.png`.

We will then use the S3 API to access data from your S3 bucket, using AWS account ID `931508227573` \(canonical ID `a2c85e730d80dcb51a2c0e1a8f852cf6dc8d6e04d9e00f49239c324de3c1e3e1`\). We generate temporary [presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html) to serve the images from your S3 bucket in our frontend. These URLs expire after 24 hours.

This setup requires that you give the Segments.ai AWS account read-only access to the data in your bucket. You can do this by granting us [cross-account access](https://aws.amazon.com/premiumsupport/knowledge-center/cross-account-access-s3/) through setting an appropriate [bucket policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html):

1. In your AWS account, go to the S3 Management Console.
2. Go to your bucket.
3. Go to the **Permissions** tab.
4. In the **Bucket Policy** section, click the **Edit** button.
5. Paste the following bucket policy and save your changes. Don't forget to replace `YOUR_BUCKET_NAME` with the name of your bucket.

```text
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

### CORS configuration

You also need to configure [CORS](https://docs.aws.amazon.com/AmazonS3/latest/userguide/cors.html) for your S3 bucket:

1. In your AWS account, go to the S3 Management Console.
2. Go to your bucket.
3. Go to the **Permissions** tab.
4. In the **Cross-origin resource sharing \(CORS\)** section, click the **Edit** button.
5. Paste the following configuration and save your changes.

```text
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "GET"
        ],
        "AllowedOrigins": [
            "https://segments.ai",
            "https://api.segments.ai"
        ],
        "ExposeHeaders": []
    }
]
```

## Google Cloud

Please [contact us](https://segments.ai/contact) to help you set this up.

## Azure

Please [contact us](https://segments.ai/contact) to help you set this up.

