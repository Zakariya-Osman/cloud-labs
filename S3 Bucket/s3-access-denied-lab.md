# S3 Bucket Access Denied Simulation Lab

## Purpose

Simulate and resolve an `AccessDenied` error in AWS S3 by manipulating bucket permissions.

---

## Step 1: Create Bucket

- Name: `cloud-labs-demo-bucket-<unique>`
- Disabled "Block all public access" (for testing only)
- Region: Default (e.g., us-east-1)

---

## Step 2: Upload File

- File uploaded: `test.txt`

---

## Step 3: Simulate Access Denied

Bucket Policy Used:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyAllAccess",
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:*",
      "Resource": [
        "arn:aws:s3:::cloud-labs-demo-bucket-<your-unique-id>",
        "arn:aws:s3:::cloud-labs-demo-bucket-<your-unique-id>/*"
      ]
    }
  ]
}
```
