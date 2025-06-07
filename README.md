# 📁 S3 Lambda File Type Detector

This AWS project demonstrates how to automatically detect and log the file type (MIME type) of any object uploaded to an S3 bucket using a Lambda function triggered by an S3 event.

Whenever a file is uploaded to the bucket, a Lambda function is triggered. It retrieves the uploaded file’s metadata and logs its MIME type and file name.

---

## 🖼️ Architecture Diagram

![Architecture](images/architecture.png) <!-- Replace this with your own image -->

---

## 🚀 Step-by-Step Guide

### 🪣 1. Create an S3 Bucket

Create a new S3 bucket that will store uploaded files and trigger the Lambda function.

📷 *Screenshot*  
![Create S3 Bucket](images/create-s3-bucket.png) <!-- Replace this with your screenshot -->

---

### ⚙️ 2. Create the Lambda Function

1. Go to AWS Lambda and create a new function (Python 3.12).
2. Paste the code from `lambda_function.py`.
3. Add a trigger connected to your S3 bucket and select "All object create events".
4. Grant the Lambda permission to access the S3 bucket (`s3:GetObject`).

📷 *Screenshot*  
![Create Lambda Function](images/create-lambda.png) <!-- Replace this with your screenshot -->

---

### 🔐 IAM Permissions Required

Make sure your Lambda execution role includes at least these permissions:

```json
{
  "Effect": "Allow",
  "Action": [
    "s3:GetObject",
    "logs:CreateLogGroup",
    "logs:CreateLogStream",
    "logs:PutLogEvents"
  ],
  "Resource": "*"
}
