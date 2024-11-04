
### 📅 Date: 2024-11-04

#### 🔍 Topic: Creating a static website using SDK and the CLI and hosting it on S3

#### 📚 Key Takeaways
**Create a static website by using Amazon S3.
**Apply a bucket policy on an S3 bucket to configure customized data protection.
**Upload objects to an S3 bucket by using the AWS SDK for Python (Boto3).
**Configure the website that is hosted on Amazon S3 to be accessible only from a specific IP address range, and test the configuration.

#### INTRODUCTION

In this project, I am using a cloud9 interface and the CLI to create a static website. I have installed python SDK that will be used to configure Amazon S3 which will host the basic website for a cafe. I have also downloaded some resources that will assist with this project from the internet using Wget. 

### 1. To create the bucket
 This is the command needed in the creation of an s3 bucket using the CLI
 




  aws iam create-policy --policy-name MyCustomPolicy --policy-document file://policy.json
