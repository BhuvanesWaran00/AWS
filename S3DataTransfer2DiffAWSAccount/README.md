# S3 Data Transfer Between Two Different AWS Accounts
## Prerequisites
+ **AWS Accounts:** You should have access to both AWS accounts involved in the data transfer process.
+ **S3 Bucket: ** Please ensure you have an S3 bucket in the source AWS account containing the data you want to transfer. And create an empty in-destination!
 AWS account
+ **IAM User:** Create an IAM user in the destination AWS account

## Steps to Transfer Data
+ Create an IAM Policy Using ```dest_IAM_Policy.json``` and Attach it with your user (remove comments before creating)
+ Goto your Source File Bucket and edit Bucket Policy using ```SF_Bucket_Policy.json``` (remove comments before creating)
+ Then config your AWS CLI using your IAM credentials
+ Run the command: aws s3 sync s3://```SFBucketName``` s3://```<DestinationBucketName>```
+ EX (OR) Output:[Screenshot 2023-08-03 145906](https://github.com/BhuvanesWaran00/AWS/assets/117109051/cda73f75-f4fe-403a-bfe3-e73ee964a397)
