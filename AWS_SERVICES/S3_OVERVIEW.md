### 📅 Date: 2024-11-04

#### 🔍 Topic: Creating a static website using SDK and the CLI and hosting it on S3

#### 📚 Key Takeaways

**Create a static website by using Amazon S3.
**Apply a bucket policy on an S3 bucket to configure customized data protection.
**Upload objects to an S3 bucket by using the AWS SDK for Python (Boto3).
**Configure the website that is hosted on Amazon S3 to be accessible only from a specific IP address range, and test the configuration.

#### INTRODUCTION

In this project, I am using a cloud9 interface and the CLI to create a static website. I have installed python SDK that will be used to configure Amazon S3 which will host the basic website for a cafe. I have also downloaded some resources that will assist with this project from the internet using Wget.By the end of this project, my architecture will end up like this:

![My architecture](<IMAGES/Screenshot 2024-11-04 123046.png>)

### 1. To create the bucket

This is the command needed in the creation of an s3 bucket using the CLI
`aws iam create-policy --policy-name MyCustomPolicy --policy-document file://policy.json`

![Creation of the bucket via CLI](<IMAGES/Screenshot 2024-11-04 124114.png>)

Next, I will set the bucket policy on the bucket by using the SDK for Python.
I have created a json file that holds the policies I want to attach to this bucket. In the part labelled ip-address, I have set my local computers ip address and so should you. This is my security measure while I do this project. The website would not load to anyone except my IP address.

![Policy document in json](<IMAGES/Screenshot 2024-11-04 125515.png>)

**Analysis:** This policy document consists of two statements. The first statement allows GetObject requests from your IP address. The second statement denies access to an object in the bucket that's named report.html, unless a specific condition is met. The report.html file doesn't exist in the bucket yet.

![python file-permissions](<IMAGES/Screenshot 2024-11-04 130311.png>)

This is the permission document that is written in python and run in the terminal. First i moved to the folder with the file and run the file as such: >python3 permissions.py

Next, I upload objects to the bucket to create the website using a simple recursive file upload command which also disables caching.

`aws s3 cp ../resources/website s3://mw-2024-11-04-s3site/ --recursive --cache-control "max-age=0"`

Once all the files are uploaded, next I will test the site and verify that it loads when a user accesses it through a virtual secure endpoint.
Finally we have this website hosted.

![Hosted Website](<IMAGES/Screenshot 2024-11-04 134047.png>)
