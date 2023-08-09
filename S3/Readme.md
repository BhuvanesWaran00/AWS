# AWS S3-Simple Storage Service
Its Storage related Service. It stores objects in buckets which means files are stored in folders, it does not have minimum charges, pay as what you can based on the bucket’s Location.
### S3 Offers
+ Scalability
+ data availability
+ Security
+ performance
+ durability
### Components
+ Buckets  - Folders / Directory
+ Object   - File
## Create Bucket \(CLI And Console)
### Create Bucket Using Console
+ Open your AWS Console
+ S3
+ Create bucket
+ Give bucket name \(Bucket Name Must Be Unique in Global level)
+ Select Bucket Region
+ Create Bucket
### Create Bucket Using CLI
+ Open Your AWS CLI
+ Use This Command: `aws s3 mb s3://<Bucket_name> --region <Region_Code>`
+ Example: `aws s3 mb s3://demo1013 --region ap-south-1`
## Upload Object \(CLI And Console)
### Upload Object Using Console
+ Goto Your Bucket
+ Upload
+ Drag and drop your resources \(or)
  + Add File / Add Folder
  + Select Your Resource in your path
+ Upload
### Upload Object Using CLI
+ Open Your AWS CLI
+ Use This Command: `aws s3 cp <Resource_Path> s3://<Bucket_name>`
+ Example: `aws s3 cp "C:Desktop\sample.txt" s3://demo1013`
## Enable Public Access for Bucket
### Public Access for Bucket
+ Goto your Bucket
+ Permission
  + Block public access (bucket settings) --> Edit --> uncheck `Block all public access` --> Save changes
  + Object Ownership --> Edit --> Select ACLs enabled --> Check `I acknowledge that ACLs will be restored.` --> Save changes
+ If you create new Bucket with public access
  + Select ACLs enabled
  + Uncheck `Block all public access`
  + Check `I acknowledge that the current settings might result in this bucket and the objects within becoming public.`
### Public Access for Object
+ Now copy your object URL and hit your Browser \(it Show is AccessDenied)
+ Click the object
+ Actions --> Make public Using ACL --> Make public
+ Now copy your object URL and hit your Browser it will show the resource
## Storage Class
Storage class | Designed for | Availability Zones | Min storage duration | Min billable object size | Monitoring and auto-tiering fees | Retrieval fees |
|--|--|--|--|--|--|--|
Standard | Frequently accessed data (more than once a month) with milliseconds access | ≥ 3 | - | - | - | - |
Intelligent-Tiering | Data with changing or unknown access patterns | ≥ 3 | - | - | Per-object fees apply for objects >= 128 KB | - |
Standard-IA | Infrequently accessed data (once a month) with milliseconds access | ≥ 3 | 30 days | 128 KB | - | Per-GB fees apply |
One Zone-IA | Recruitable, infrequently accessed data (once a month) stored in a single Availability Zone with milliseconds access | 1 | 30 days | 128 KB | - | Per-GB fees apply |
Glacier Instant Retrieval | Long-lived archive data accessed once a quarter with instant retrieval in milliseconds | ≥ 3 | 90 days | 128 KB | - | Per-GB fees apply |
Glacier Flexible Retrieval (formerly Glacier) | Long-lived archive data accessed once a year with retrieval of minutes to hours | ≥ 3 | 90 days | - | - | Per-GB fees apply |
Glacier Deep Archive | Long-lived archive data accessed less than once a year with retrieval of hours | ≥ 3 | 180 days | - | - | Per-GB fees apply |
Reduced redundancy | Noncritical, frequently accessed data with milliseconds access (not recommended as S3 Standard is more cost effective) | ≥ 3 | - | - | - | Per-GB fees apply |
## Setup Versioning
### Versioning Introduction
+ Versioning in Amazon S3 is a means of keeping multiple variants of an object in the same bucket.
+ With versioning, you can recover more easily from both unintended user actions and application failures.
+ After versioning is enabled for a bucket, if Amazon S3 receives multiple write requests for the same object simultaneously, it stores all of those objects.
+ Versioning-enabled buckets can help you recover objects from accidental deletion or overwrite. For example, if you delete an object, Amazon S3 inserts a delete marker instead of removing the object permanently. The delete marker becomes the current object version. If you overwrite an object, it results in a new object version in the bucket. You can always restore the previous version.
### Enable Versioning
+ Enable versioning in creating bucket \(or)
+ For an existing bucket `open bucket --> Properties --> Edit --> Enable --> Save changes`
## Setup Cross-Region Replication
+ Create Two buckets in different regions
  + Bucket 1: region - `us-east-1 ` \(with Source Files)
  + Bucket 2: region - `us-east-2` \(it's destination bucket)
+ Enable Replication in Source Bucket and add a rule
    + Goto bucket --> Management --> 
    + Goto bucket --> Management --> Replication rules \(Create replication rule) --> Name Replication rule --> click `Apply to all objects in the bucket` --> Destination \(Browse S3 \(Select target Bucket)) --> Choose path --> Enable Versioning --> In IAM Role (Select Create New Role) --> Check `Replicate objects encrypted with AWS Key Management Service (AWS KMS)` --> In `AWS KMS keys for decrypting source objects` Check the Box -->  Select `Choose from your AWS KMS keys` --> In `Available AWS KMS keys` Select Key which one is showing --> Select Storage class `one zone IA` --> save
    + Select `Yes, replicate existing objects.` --> Submit
+ Wait for 3 - 5 min then refresh your target Bucket
+ Now File transferred to your S3 Buckets
## Introduction to S3 lifecycle policy
To manage your objects so that they are stored cost-effectively throughout their lifecycle, configure their Amazon S3 Lifecycle. An S3 Lifecycle configuration is a set of rules that define actions that Amazon S3 applies to a group of objects. <br>
There are two types of actions: <br>
+ **Transition actions** – These actions define when objects transition to another storage class.
+ **Expiration actions** - Amazon S3 deletes expired objects on your behalf.
### Steps to Create a Life Cycle Policy
+ Goto your bucket
+ Management --> Create lifecycle rule
+ Name Your Life Cycle Rule --> Select Lifecycle rule actions which you want --> Edit Action Which you want --> Create Rule 
## Static Website Hosting
+ Create a Public & ACL Enabled bucket
+ Upload Web Files
+ Properties --> Static website hosting
  + Static website hosting - enable
  + Hosting type - Host a static website
  + Index document - Index File Name
  + Save changes
+ Copy the URL: `EX: http://datatans20.s3-website-us-east-1.amazonaws.com`
+ Permission --> Bucket policy --> Copy Paste Below Policy
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Allow_Public_Permission",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::datatans20/*"
            //Resource": "arn:aws:s3:::datatans20/*
        }
    ]
}
```
+ Hit URL into your browser
