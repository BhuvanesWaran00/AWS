# Amazon Kinesis Data Firehose delivery stream be configured to transmit real-time analytics data to an Amazon DynamoDB table
Amazon Kinesis Data Firehose can be configured to transmit real-time analytics data to an Amazon DynamoDB table, enabling seamless data flow, rapid storage, and analytics.
This involves orchestrating AWS components for efficient data delivery and storage in DynamoDB, enhancing real-time insights from streaming data.

## Amazon Kinesis Data Firehose
Amazon Kinesis Data Firehose is an extract, transform, and load (ETL) service that reliably captures, transforms, and delivers streaming data to data lakes,
data stores, and analytics services.

![kinesis](https://github.com/BhuvanesWaran00/AWS/assets/117109051/5bd8df1e-2a03-4835-9ce0-75d5b7a9fd52)

The diagram outlines capturing, transforming, and delivering streaming data using Amazon Kinesis Data Firehose, with six written steps and six illustrated sets.

  1. The initial step, "Input," details various input sources like logs, clickstreams, IoT, financial data, and sales orders, with an initial illustration of a database, server, and document.

  2. The second step, "Ingest," lists data sources from AWS SDK, Kinesis Data Streams, Amazon Kinesis Agent, over 20 AWS services, and Open Source Agent, with illustrated icons.

  3. The third step, "Amazon Kinesis Data Firehose," provides a fully managed Ingest, Transform, Load (ITL) solution without the need for code, illustrating a firehose.

  4. The fourth step, "Transform (optional)," includes using AWS Lambda Custom Transformations and Built-In Transformations, with illustrations featuring AWS Lambda icons and a gear.

  5. The fifth step, "Load," lists various loading tools like Amazon S3, Amazon Redshift, Amazon OpenSearch Service, Amazon API Gateway, Splunk, and over six HTTP Endpoint Partners.

  6. The sixth step, "Output," involves analyzing streaming data using interactive query services or analytics tools, with a set of graphs as an illustration.

### Configuration Of Kinesis
1. Create a S3 Bucket (i.e. same region as the Kinesis data stream).
   ![Screenshot 2023-09-20 120616](https://github.com/BhuvanesWaran00/AWS/assets/117109051/ac7055c1-5c24-472c-afc4-765c4c7414f1)
2. Goto Amazon Kinesis Dashboard --> Select Kinesis Data Firehose --> Create delivery stream
   ![Screenshot 2023-09-20 121128](https://github.com/BhuvanesWaran00/AWS/assets/117109051/46036155-0b2a-4947-a6ea-b12a2629517a)
3. Under Choose source and destination,
  - Source: Choose Direct PUT
  - Destination: Choose Amazon S3
  - Delivery stream name, give a name of your choice.
    ![Screenshot 2023-09-20 122341](https://github.com/BhuvanesWaran00/AWS/assets/117109051/c52c8a42-8fc3-4e51-aa97-ca15c8d2ac12)
  - select the S3 Bucket you created earlier,
  - S3 bucket prefix: give-name/
  - S3 bucket error output prefix: give-name/
    ![Screenshot 2023-09-20 122436](https://github.com/BhuvanesWaran00/AWS/assets/117109051/4a123729-2340-49b2-80b9-b5f7cd3f8198)
    ![Screenshot 2023-09-20 122446](https://github.com/BhuvanesWaran00/AWS/assets/117109051/e090cbd9-b108-42b5-a23a-223fe42a36a0)
  - Advanced settings --> Create or update the IAM role.
    ![Screenshot 2023-09-20 122456](https://github.com/BhuvanesWaran00/AWS/assets/117109051/a796b839-c1f7-48dd-88e7-5910f34b1f2a)
  - Create a delivery stream (It will take si=ome minutes)
    ![Screenshot 2023-09-20 123933](https://github.com/BhuvanesWaran00/AWS/assets/117109051/a2f45ddc-9fff-4ab8-89cd-3eb7e84a9193)
    
### Testing Firehose
  - Expand the Test with demo data --> Start sending demo data
    ![Screenshot 2023-09-20 124334](https://github.com/BhuvanesWaran00/AWS/assets/117109051/b421f6c6-744e-4aa4-a762-e9ef4bd8cc4e)
  - Now open your bucket and verify data
    ![Screenshot 2023-09-20 124820](https://github.com/BhuvanesWaran00/AWS/assets/117109051/dd67592b-1f2a-4d2c-948b-1f4b197aa3c2)
  - Stop sending demo data







 


