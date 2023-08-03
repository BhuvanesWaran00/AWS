# S3 Data Transfer Between Two Different AWS Accounts
## Prerequisites
+ **AWS Accounts:** You should have access to both AWS accounts involved in the data transfer process.
+ **S3 Bucket:** Ensure that you have an S3 bucket in the source AWS account containing the data you want to transfer. And create empty in destination AWS account
+ **IAM User:** Create a IAM user in destination AWS account

## Steps to Transfer Data
+ Create a IAM Policy Using [dest_IAM_Policy.json] and Attach with your user (remove comments before create)
+ Goto your Source File Bucket and edit Bucket Policy using [SF_Bucket_Policy.json] (remove comments before create)
+ Then config your AWS CLI using your IAM credentials
+ Run the commend: aws s3 sync s3://<SFBucketName> s3://<DestinationBucketName>