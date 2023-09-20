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
  - Now open your bucket and verify the data
    ![Screenshot 2023-09-20 124820](https://github.com/BhuvanesWaran00/AWS/assets/117109051/dd67592b-1f2a-4d2c-948b-1f4b197aa3c2)
  - Stop sending demo data

## Amazon DynamoDB
Amazon DynamoDB is a fully managed, serverless, key-value NoSQL database designed to run high-performance applications at any scale. DynamoDB offers built-in security, continuous backups, automated multi-region replication, in-memory caching, and data import and export tools.
   ![DynamoDB](https://github.com/BhuvanesWaran00/AWS/assets/117109051/747747e0-b4d9-46d5-a828-cf0b9e0b1a7f)

The diagram displays the fundamental features of Amazon DynamoDB and its integrations with other AWS services, arranged in three sections from left to right.

  1. The DynamoDB service icon is displayed in a box labeled"Configure Key Features."The box contains six boxes, each with three rows, representing features such as NoSQL Workbench, encryption at rest, on-demand capacity mode, Global Tables, point-in-time recovery, and PartiQL supports. Additional DynamoDB features are listed below each box, with a sentence below the "Configure Key Features" heading.

  2. The second section features a magnifying glass displaying data blocks, with a left arrow representing DynamoDB data and a right arrow representing data from AWS services. The headline "Export, Analyze, Stream Data" explains the functions available when integrating with other AWS services.
  
  3. The third section contains five boxes representing DynamoDB's integrations: Amazon S3, AWS Glue Elastic Views, Amazon Kinesis Data Streams, AWS CloudTrail, and Amazon Cloudwatch, each containing a different service.

### Configure Table in DynamoDB
1. DynamoDB Dashboard --> Create table
    1. Table name: give a name of your choice.
    2. Partition key: give a name and type related to your table.
       ![Screenshot 2023-09-20 131927](https://github.com/BhuvanesWaran00/AWS/assets/117109051/78642ad9-5fb0-416f-b840-5ba14bfe7cb9)
2. Create table
   ![Screenshot 2023-09-20 132305](https://github.com/BhuvanesWaran00/AWS/assets/117109051/f6e5d65f-efad-403a-aead-ab0855af24f5)
3. Explore table items --> Create item
   ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/1327a59d-003b-4993-9d43-c3a431974f48)
4. Enter table data if you want to add an Attribute name
   - click Add a new attribute
   - Select Type enter details
     ![Screenshot 2023-09-20 134416](https://github.com/BhuvanesWaran00/AWS/assets/117109051/11868574-d10b-4938-b4b5-8669b754644f)
5. Create item
   ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/c7a9e2aa-4e67-4bf3-af3e-51ba53493fe4)
### Fetch Data using Scan and Query
- Select the “Scan” option (which is in the left upper corner). --> Select Table --> Run
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/e7e5017f-6942-41a1-ba77-796f364f478a)
- Select the “Query” option (which is in the left upper corner). --> Select Table --> enter data which you want --> Run
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/92cc493e-8c21-4e25-a631-bef7dc9b88ed)

## Real-time Analytics and Data Streaming

### Analytics
1. Real-time analytics processes data as it's generated, enabling swift decision-making.
2. Streaming data from sources like IoT devices is a key input for real-time analytics.
3. Low latency is essential, with data analyzed within milliseconds or seconds.
4. Common use cases include fraud detection, e-commerce personalization, and patient monitoring.
5. Stream processing frameworks like Apache Kafka and Spark are used for data processing.
6. Visualization through dashboards offers real-time insights into performance metrics.
7. Machine learning models enhance analytics by predicting trends and anomalies.
8. Scalability and data quality are crucial for efficient and accurate analysis.
9. Security measures protect sensitive data in real-time analytics systems.
10. Ongoing monitoring and optimization ensure the system's effectiveness over time.

### Data Streaming
1. Data streaming is the continuous flow of real-time or near-real-time data from diverse sources.
2. It uses protocols like MQTT, Apache Kafka, or HTTP/HTTPS for data transmission.
3. Data can be structured, unstructured, or semi-structured, making it versatile.
4. Stream processing frameworks enable real-time transformations and analytics.
5. Key applications include IoT, fraud detection, and social media monitoring.
6. Scalability is crucial to handle high data volumes efficiently.
7. Data quality and low latency are essential for accurate analysis.
8. Integration with databases and analytics engines enhances insights.
9. Fault tolerance and cost management are important considerations.
10. Data streaming empowers organizations to make informed decisions in real time.
