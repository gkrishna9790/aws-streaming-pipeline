# Tutorial: Build a streaming data pipeline in AWS

Streaming Data is data that is generated continuously by thousands of data sources, which typically send in the data records simultaneously, and in small sizes (order of Kilobytes). Streaming data includes a wide variety of data such as log files generated by customers using your mobile or web applications, ecommerce purchases, in-game player activity, information from social networks, financial trading floors, or geospatial services, and telemetry from connected devices or instrumentation in data centers.

### 1. Key AWS Services for building a Streaming Data Pipeline

To start with, AWS provides some powerful offering to ingest, process and deliver streaming data. The most popular 
AWS managed service is [Kinesis](https://aws.amazon.com/kinesis/).

Kinesis is comprised of four main components:  

I. [**Kinesis Data Streams**](https://aws.amazon.com/kinesis/data-streams/): Kinesis streams can continuously capture gigabytes of data per second from hundreds of thousands of sources.
The main component of a Kinesis data stream is a **shard**. A shard is a uniquely identified sequence of data records in a stream. A stream is composed of one or more shards, each of which provides a fixed unit of capacity.
Inorder to build your first, Kinesis Stream:

   1. Log into the AWS console, and search for Kinesis amongst the applications. It can be found under the 'Analytics' section. 
   2. Under Kinesis data streams, click on '**Create data stream**'
   3. Name your first Kinesis stream (please provide some meaningful name)
   4. Add the number of shards required in the bottom section of the page as shown below: 
   ![KDS](https://github.com/gkrishna9790/aws-streaming-pipeline/blob/master/images/kds.JPG)
   5. Click on 'Create Kinesis Stream' button 
   
   ***Note:*** *Each shard can support upto 1000 records per second, with a maximum write capacity of 1 MB of data per second, and read data at a rate of*
   *2 MB per second. Depending on the estimated size of data that flows in, configure the number of shards required.* 
   
   ***For the purpose of this demo, a single shard should suffice.***
   
   Now you have a fully functional Kinesis stream capable of ingesting real-time data. Yaaay !!! Each stream can retain the data for a default periof of 24 hours, which can be increased upto 7 days at an extra cost. 
   
II. [**Kinesis Data Analytics**](https://aws.amazon.com/kinesis/data-analytics/): Amazon Kinesis Data Analytics reduces the complexity of building, managing, and integrating streaming applications with other AWS services. SQL users can easily query streaming data or build entire streaming applications using templates and an interactive SQL editor. 

**Note**: Kinesis Analytics is more of an ETL tool for real-time data. It let's you connect a source, do necessary transformations (data-types, field names, etc.) and create a transformed data for delivery all in real-time. That's pretty cool right? 

Inorder to build the Kinesis Analytics application, come back to Kinesis dashboard, click on Data Analytics and:
1. Click on 'Create application'
2. Add name and description to your application and hit 'Create application'
3. Click on 'Connect streaming data' and choose the stream you created in the previous section
4. You can edit the schema on the fly using 'Discover schema'
5. Hit 'Save and Continue' at the bottom of the screen. 
6. Now you have connected your source pipeline

Now to do the transformation part, under 'Real time analytics' click on 'Go to SQL editor'. 
1. You'll see a window to type your code.
2. You can provide your code in SQL like fashion. 
3. Kinesis Analytics let's your create multiple target streams from a single input stream.
4. Once you provide the SQL Query, you can hit 'Start Application'

Kinesis Analytics Terminology:
1. Streams - the basic source/destination of data (comparable to a table in relational database concept)
2. Pump - to insert data into a stream (a term for insert statement in rel. database world)

So, you basically create a stream(table), create a pump to insert data into the stream from the source stream

