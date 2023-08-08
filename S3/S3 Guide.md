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
  

