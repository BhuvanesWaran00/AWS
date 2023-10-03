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
  - Create a delivery stream (It will take some minutes)
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

## Integration and Data Flow
### Integration
Integration involves making different systems or applications work together as a unified whole. It aims to create a cohesive environment where data and processes can be shared seamlessly.

### Types of Integration:
- Data Integration
- Application Integration
- Business Process Integration

### Key Components:
- **Connectors:** Interface components that facilitate communication between different systems.
- **Middleware:** Software that acts as a bridge between applications, allowing them to communicate and share data.
- **APIs (Application Programming Interfaces):** Specifies how different software components should interact.

### Data Flow
Data Flow describes the movement of data from one location or application to another. It encompasses the entire journey of data through a system.

### Key Concepts:
- **Source:** The location or application where data originates.
- **Transformation:** The process of modifying or converting data as it moves through the system.
- **Destination:** The final location or application where the data is intended to reside.

### Data Flow Steps:
- **Ingestion:** The process of bringing data into a system.
- **Processing:** Manipulating or transforming data as it moves through the system.
- **Storage:** Storing data for future use or reference.
- **Analysis:** Extracting insights or patterns from the data.
- **Visualization:** Presenting data in a human-readable format for analysis or decision-making.

There isn't a standard way of inserting Firehose stream data into DynamoDB (such as S3 or Redshift). The recommended way is to do a Lambda and insert the records into DynamoDB with that. Use dynamoDB. batchWriteItem or dynamoDB

![Flow of Intergration](https://github.com/BhuvanesWaran00/AWS/assets/117109051/54f18cdb-65b1-487f-9f1c-f10607d98ec5)

## Best Practices
- Consider increasing batch size for DynamoDB writes to reduce per-item write costs.
- Implement the principle of least privilege for the IAM role used by Kinesis Data Firehose.
- Grant only the necessary permissions to write to the specific DynamoDB table
- Set up CloudWatch Alarms to monitor key metrics such as delivery errors, buffer utilization, and data transformation success rates.

## Use Cases and Examples
### Real-Time E-commerce Analytics:
**Use Case:** Track user behavior, purchase patterns, and product popularity in real time.
**Example:** Capture and analyze clickstream data, user interactions, and transaction details to provide personalized recommendations.

### Streaming Analytics for Gaming:
**Use Case:** Analyze real-time gaming data for player insights and behavior.
**Example:** Ingest gaming events, such as player movements and interactions, and store them in DynamoDB for player profiling and game optimization.

### Social Media Sentiment Analysis:
**Use Case:** Monitor and analyze social media feeds for sentiment in real-time.
**Example:** Ingest social media posts, perform sentiment analysis, and store the results in DynamoDB for trend analysis and reporting.

## Conclusion:
Configuring Amazon Kinesis Data Firehose to transmit real-time analytics data to Amazon DynamoDB provides ptimizing configurations based on usage patterns. It contributes to cost-effectiveness in terms of both data storage and processing. The ability to use AWS Lambda functions for data transformation provides flexibility in preparing and enriching data before it reaches DynamoDB.

## References
[AWS Kinesis](https://aws.amazon.com/kinesis/) <br>
[AWS Kinesis Data Firehose](https://aws.amazon.com/kinesis/data-firehose/) <br>
[AWS DynamoDB](https://aws.amazon.com/dynamodb/) <br>
[AWS Lambda](https://aws.amazon.com/lambda/)

## Appendices
**Integration Workflow Diagram:** A visual representation of the end-to-end integration workflow, illustrating the flow of data from the source through Kinesis Data Firehose to DynamoDB.

**Real-Time Analytics Results Screenshots:** Screenshots or results from real-time analytics performed on data stored in DynamoDB, showcasing the practical value derived from the solution.

