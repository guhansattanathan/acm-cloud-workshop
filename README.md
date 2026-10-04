# AWS S3 Cloud Workshop

In this workshop, you will deploy a simple static website using Amazon S3.

## 1. Create an AWS Account

Go to [AWS](https://aws.amazon.com/) and create an account.

AWS currently provides new accounts with Free Tier benefits and credits. You should not need to pay for this workshop if you stay within the available free usage and credits.

## 2. Open S3

1. Sign in to the AWS Console.
2. Search for **S3**.
3. Select **S3**.
4. Click **Create bucket**.

## 3. Create Your Bucket

Use these settings:

*   **AWS Region:** US East (Ohio) `us-east-2`
*   **Bucket type:** General purpose
*   **Bucket namespace:** Global namespace
*   **Bucket name:** Choose a unique name
*   **Object Ownership:** Bucket owner enforced
*   **Block all public access:** Turn **OFF**
*   **Bucket Versioning:** Disable
*   **Tags:** None
*   **Encryption:** Server-side encryption with Amazon S3 managed keys (SSE-S3)
*   **Bucket Key:** Disable

Click **Create bucket**.

## 4. Upload the Website

Open your bucket and click **Upload**.

Upload the following files:

```text
index.html
style.css
```

Make sure both files are directly inside the bucket.

## 5. Enable Static Website Hosting

1. Open your bucket.
2. Go to **Properties**.
3. Find **Static website hosting**.
4. Click **Edit**.
5. Select **Enable**.
6. Select **Host a static website**.
7. Set the Index document to: `index.html`
8. Save the changes.

AWS will provide a Bucket website endpoint. You will use this URL to access your website.

## 6. Allow Public Access

1. Go to: **Permissions** > **Block public access**
2. Make sure **Block all public access** is turned off.

This is required because the website needs to be accessible from the internet.

## 7. Add a Bucket Policy

1. Go to: **Permissions** > **Bucket policy** > **Edit**
2. Paste the following policy. Replace `YOUR-BUCKET-NAME` with your actual bucket name:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
        }
    ]
}
```

Click **Save changes**.

## 8. View Your Website

1. Go back to: **Properties** > **Static website hosting**
2. Click the Bucket website endpoint.

Your website should now be publicly accessible. Try changing your HTML locally, uploading the updated file to S3, and refreshing the website.

## Cost and Security

*   AWS services can incur charges depending on usage.
*   This workshop is designed to use very little AWS resources, but AWS pricing and Free Tier policies can change.
*   Do not create resources that are not required for this workshop.
*   Delete your S3 bucket and its contents when you are finished.
*   The bucket policy above makes the website files publicly readable.
*   Do not upload passwords, API keys, personal information, or other sensitive files.
*   Keep your AWS account credentials private.
*   Do not share your AWS account password or access keys with anyone.
*   For this workshop, we are using S3 to demonstrate how cloud storage can be used to host a simple website.