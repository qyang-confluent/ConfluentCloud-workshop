<div align="center">
    <img src="images/gartner.png" width=25% height=25%>
</div>


<div align="center">
    <img src="images/confluent.png" width=50% height=50%>
</div>


# <div align="center">Gartner Demo and Workshop repository</div>

This repository contains workshop content for Gartner to be held on April 3rd.  Content with the lab instructions and hands-on guide will be updated before the workshop. Please see below for the details of the workshop and agenda: 

## Introduction

Today’s modern customers value an end-to-end real-time experience. Businesses that are able to deliver real-time, personalized experiences need to be connected and fueled at all times by a constant supply of real-time event streams and continuous real-time processing. They need access to data in motion.

We welcome you to join the Confluent team in a workshop to get started with data in motion. Each session includes a virtual guided workshop on how you can use Confluent Cloud to explore event-driven architectures and how these measured and well-informed architectural decisions result in successful outcomes. 

This workshop is perfect for those looking to get started with Confluent Cloud and build the foundation of your use case with our experienced engineers. 


## Workshop Agenda - Day 1:

| Topic | Time (US Eastern) | Speaker |
| --- | --- | --- |
| Workshop Kickoff | 8:00 - 8:15 | Eric Langan - Confluent |
| Review Gartner Use-Cases and <br/> Architecture |  8:15 - 9:00  | Eric Langan / Qi Yang - Confluent |
| Break |  9:00 - 9:15  |  |
| Confluent Introduction and <br/> Hands-on Workshop Demo |  9:15 - 10:45  | Qi Yang - Confluent |
| Workshop Environment setup/Break |  10:45 - 11:30  | Gartner team |
| AWS MSK and Confluent Cloud|  11:30 - 12:00  | Joseph Morais, Staff Partner Solutions Engineer |
| Observability and Monitoring |  12:00 - 12:45  | Dustin Cote, Senior Product Manager  |


 


## Workshop Agenda - Day 2:

| Topic | Time | Speaker |
| --- | --- | --- |
| MVP Evaluation Roadmap |  8:00 - 9:00  |  Gartner Team  |
| Break |  9:00 - 9:15  |  |
| Value Assessment |  9:15 - 10:00  |  Eric Langan  |
| Stream Lineage and Data Governance |  10:00 - 11:00  | David Araujo, Staff Product Manager  |
| Q&A and Workshop wrap-up |  11:00 - 12:00  | Eric Langan / Qi Yang - Confluent |



## Topics Covered in the Demo and Workshop:
1. [Log into Confluent Cloud](#step-1)
2. [Create an Environment and Cluster](#step-2)
3. [Create ksqlDB Application](#step-3)
4. [Create Topics and walk through Confluent Cloud Dashboard](#step-4)
5. [Create an API Key Pair](#step-5)
6. [Create Datagen Connectors for Users and Stocks](#step-6)
7. [Create a Stream and a Table](#step-7)
8. [Create a Persistent Query](#step-8)
9. [Aggregate data](#step-9)
10. [Windowing Operations and Fraud Detection](#step-10)
11. [Pull Queries](#step-11)
12. [Enable Schema Registry](#step-12)
13. [Cloud ETL Example](#step-13)
14. [Sink Connector to Redshift](#step-14)
15. [Enable Cluster Linking](#step-15)
16. [Observability and Monitoring](#step-16)
17. [Clean Up Resources](#step-17)
18. [Confluent Resources and Further Testing](#step-18)

***

## **Prerequisites**
<br>

1. Create a Confluent Cloud Account.
    - Please make sure that you are able to successfully login to Confluent Cloud before the workshop.
> **Note:** You will create resources during this workshop that will incur costs. Please make sure that you monitor resource usage to stay within the credits offered for this workshop and POC evaluation. 


## <a name="step-1"></a>Log into Confluent Cloud

1. Log into [Confluent Cloud](https://confluent.cloud) and enter your email and password.

<div align="center" padding=25px>
    <img src="images/login.png" width=50% height=50%>
</div>

2. If you are logging in for the first time, you will see a self-guided wizard that walks you through spinning up a cluster. Please minimize this as you will walk through those steps in this workshop. 

***

## <a name="step-2"></a>Create an Environment and Cluster

An environment contains clusters and its deployed components such as Connectors, ksqlDB, and Schema Registry. You have the ability to create different environments based on your company's requirements. For example, you can use environments to separate Development/Testing, Pre-Production, and Production clusters. 

1. Click **+ Add Environment**. Specify an **Environment Name with your Initials** and Click **Create**. 

>**Note:** There is a *default* environment ready in your account upon account creation. You can use this *default* environment for the purpose of this workshop if you do not wish to create an additional environment.

<div align="center" padding=25px>
    <img src="images/environment.png" width=50% height=50%>
</div>

2. Now that you have an environment, click **Create Cluster**. 

> **Note:** Confluent Cloud clusters are available in 3 types: Basic, Standard, and Dedicated. Basic is intended for development use cases so you will use that for the workshop. Basic clusters only support single zone availability. Standard and Dedicated clusters are intended for production use and support Multi-zone deployments. If you are interested in learning more about the different types of clusters and their associated features and limits, refer to this [documentation](https://docs.confluent.io/current/cloud/clusters/cluster-types.html).

3. Chose the **Basic** cluster type. 

<div align="center" padding=25px>
    <img src="images/cluster-type.png" width=50% height=50%>
</div>

4. Click **Begin Configuration**. 
5. Choose your preferred Cloud Provider (AWS, GCP, or Azure), region, and availability zone. 
6. Specify a **Cluster Name**. For the purpose of this lab, any name will work here. 

<div align="center" padding=25px>
    <img src="images/create-cluster.png" width=50% height=50%>
</div>

7. View the associated *Configuration & Cost*, *Usage Limits*, and *Uptime SLA* information before launching. 
8. Click **Launch Cluster**. 

***

## <a name="step-3"></a>Create a ksqlDB Application

1. On the navigation menu, select **ksqlDB** and click **Create Application Myself**. 
2. Select **Global Access** and then **Continue**.
3. Name you ksqlDB application and set the streaming units to **4**. Click **Launch Application!**

> **Note:** A Confluent Streaming Unit is the unit of pricing for Confluent Cloud ksqlDB. A CSU is an abstract unit that represents the size of your kSQL cluster and scales linearly. 

<div align="center" padding=25px>
    <img src="images/create-application.png" width=50% height=50%>
</div>

***

## <a name="step-4"></a>Creates Topic and Walk Through Cloud Dashboard

1. On the navigation menu, you will see **Cluster Overview**. 

> **Note:** This section shows Cluster Metrics, such as Throughput and Storage. This page also shows the number of Topics, Partitions, Connectors, and ksqlDB Applications.  Below is an example of the metrics dashboard once you have data flowing through Confluent Cloud. 

<div align="center" padding=25px>
    <img src="images/cluster-metrics.png" width=75% height=75%>
</div>

2. Click on **Cluster Settings**. This is where you can find your *Cluster ID, Bootstrap Server, Cloud Details, Cluster Type,* and *Capacity Limits*.
3. On the same navigation menu, select **Topics** and click **Create Topic**. 
4. Enter **users_topic** as the topic name, **1** as the number of partitions, and then click **Create with defaults**. 

<div align="center" padding=25px>
    <img src="images/create-topic.png" width=50% height=50%>
</div>

5. Repeat the previous step and create a second topic name **stocks_topic** and **1** as the number of partitions. 

> **Note:** Topics have many configurable parameters. A complete list of those configurations for Confluent Cloud can be found [here](https://docs.confluent.io/cloud/current/using/broker-config.html). If you are interested in viewing the default configurations, you can view them in the Topic Summary on the right side. 

6. After topic creation, the **Topics UI** allows you to monitor production and consumption throughput metrics and the configuration parameters for your topics. When you begin sending messages to Confluent Cloud, you will be able to view those messages and message schemas.
7. Below is a look at the topic, **users_topic**, but you need to send data to this topic before you see any metrics.

<div align="center" padding=25px>
    <img src="images/users-topic.png" width=75% height=75%>
</div>

***

## <a name="step-5"></a>Create an API Key Pair

1. Select **API Access** on the navigation menu. 
2. A key pair has already been created for the ksqlDB application you created in *Step 3*. Select **+ Add Key** to create another key pair. 

<div align="center" padding=25px>
    <img src="images/create-key.png" width=75% height=75%>
</div>

3. Select **Global Access** and then click **Next**. 
4. Copy or save your API Key and Secret somewhere. You will need these later on in the lab, you will not be able to view the secret again once you close this dialogue. 
5. After creating and saving the API key, you will see this API key in the Confluent Cloud UI in the **API Access** tab. If you don’t see the API key populate right away, refresh the browser.

***

## <a name="step-6"></a>Create Datagen Connectors for Users and Stocks

The next step is to produce sample data using the Datagen Source connector. You will create two Datagen Source connectors. One connector will send sample user data to **users_topic** and the other connector will send sample stock data to **stocks_topic**.

1. First, you will create the connector that will send data to **users_topic**. From the Confluent Cloud UI, click on the **Connectors** tab on the navigation menu. Click on the **Datagen Source** icon.

<div align="center" padding=25px>
    <img src="images/connectors.png" width=75% height=75%>
</div>

2. Enter the following configuration details. The remaining fields can be left blank.

<div align="center">

| setting                            | value                        |
|------------------------------------|------------------------------|
| name                               | DatagenSourceConnector_Users |
| api key                            | [*from step 5* ](#step-5)    |
| api secret                         | [*from step 5* ](#step-5)    |
| topic                              | users_topic                  |
| output message format              | JSON                         |
| quickstart                         | USERS                        |
| max interval between messages (ms) | 1000                         |
| tasks                              | 1                            |
</div>

<br>

3. Click on **Next**.
4. Before launching the connector, you should see something similar to the following. If everything looks similar, select **Launch**. 

<div align="center" padding=25px>
    <img src="images/add-datagen-conn.png" width=50% height=50%>
</div>

5. Next, create the second connector that will send data to **stocks_topic**. Click on **+ Add Connector** and then the **datagen Source** icon again. 

6. Enter the following configuration details. The remaining fields can be left blank. 

<div align="center">

| setting                            | value                        |
|------------------------------------|------------------------------|
| name                               | DatagenSourceConnector_Stocks|
| api key                            | [*from step 5* ](#step-5)    |
| api secret                         | [*from step 5* ](#step-5)    |
| topic                              | stocks_topic                 |
| output message format              | JSON                         |
| quickstart                         | STOCKS                       |
| max interval between messages (ms) | 1000                         |
| tasks                              | 1                            |
</div>

<br> 

7. Review the output again and then select **Launch**.

> **Note:** It may take a few moments for the connectors to launch. Check the status and when both are ready, the status should show *running*. <br> <div align="center"><img src="images/running-connectors.png" width=75% height=75%></div>

> **Note:** If the connectors fails, there are a few different ways to troubleshoot the error:
> * Click on the *Connector Name*. You will see a play and pause button on this page. Click on the play button.
> * Click on the *Connector Name*, go to *Settings*, and re-enter your API key and secret. Double check there are no extra spaces at the beginning or end of the key and secret that you may have accidentally copied and pasted.
> * If neither of these steps work, try creating another Datagen connector.


9. You can view the sample data flowing into topics in real time. Navigate to  the **Topics** tab and then click on the **users_topic**. You can view the production and consumption throughput metrics here.

<div align="center">
    <img src="images/users-topic-overview.png" width=75% height=75%>
</div>

10. Click on **Messages**. In the search bar, select **Jump to Offset** from the drop-down, set the offset to **0**, and then execute the search. 

* You should now be able to see the messages within the UI. You can toggle between the table and payload views of the events by clicking the following buttons. 

<div align="center">
    <img src="images/card-view.png">
</div> 

* The messages should look something like the following. 

<div align="center">
    <img src="images/card-view-values.png" width=75% height=75%>
</div>


***

## <a name="step-7"></a>Create a Stream and a Table

Now that you are producing a continuous stream of data to **users_topic** and **stocks_topic**, you will use ksqlDB to understand the data better by performing continuous transformations, masking certain fields, and creating new derived topics with the enriched data.

You will start by creating a stream and table, which will be the foundation for your transformations in the upcoming steps.

A *stream* provides immutable data. It is append only for new events; existing events cannot be changed. Streams are persistent, durable, and fault tolerant. Events in a stream can be keyed.

A *table* provides mutable data. New events—rows—can be inserted, and existing rows can be updated and deleted. Like streams, tables are persistent, durable, and fault tolerant. A table behaves much like an RDBMS materialized view because it is being changed automatically as soon as any of its input streams or tables change, rather than letting you directly run insert, update, or delete operations against it.

To learn more about *streams* and *tables*, the following resources are recommended:
- [Streams and Tables in Apache Kafka: A Primer](https://www.confluent.io/blog/kafka-streams-tables-part-1-event-streaming/)
- [ksqlDB: Data Definition](https://docs.ksqldb.io/en/latest/reference/sql/data-definition/)

<br>

1. Navigate back to the **ksqlDB** tab and click on your application name. This will bring us to the ksqlDB editor. 

> **Note:** You can interact with ksqlDB through the **Editor**. You can create a stream by using the `CREATE STREAM` statement and a table using the `CREATE TABLE` statement. <br><br>To write streaming queries against **users_topic** and **stocks_topic**, you will need to register the topics with ksqlDB as a stream and/or table. 

2. First, create a **Stream** by registering the **stocks_topic** as a stream called **stocks_stream**. 

```sql
CREATE STREAM stocks_stream (
    side varchar, 
    quantity int, 
    symbol varchar, 
    price int, 
    account varchar, 
    userid varchar
) 
WITH (kafka_topic='stocks_topic', value_format='JSON');
```

3. Next, go to the **Streams** tab at the top and click on **STOCKS_STREAM**. This provides information on the stream, output topic (including replication, partitions, and key and value serialization), and schemas.

<div align="center">
    <img src="images/stream-detail.png" width=50% height=50%>
</div>

4. Click on **Query Stream** which will take you back to the **Editor**. You will see the following query auto-populated in the editor which may be already running by default. If not, click on **Run query**. To see data already in the topic, you can set the `auto.offset.reset=earliest` property before clicking **Run query**. <br> <br> Optionally, you can navigate to the editor and construct the select statement on your own, which should look like the following.

```sql
SELECT * FROM STOCKS_STREAM EMIT CHANGES;
```

5. You should see the following data within your **STOCKS_STREAM** stream.

<div align="center">
    <img src="images/stocks-stream-select-results.png" width=75% height=75%>
</div>

6. Click **Stop**. 
7. Next, create a **Table** by registering the **users_topic** as a table named **users**. Copy the following code into the **Editor** and click **Run**. 

```sql
CREATE TABLE users (
    userid varchar PRIMARY KEY, 
    registertime bigint, 
    gender varchar, 
    regionid varchar
) 
WITH (KAFKA_TOPIC='users_topic', VALUE_FORMAT='JSON');
```

8. Once you have created the **USERS** table, repeat what you did above with **STOCKS_STREAMS** and query the **USERS** table. This time, select the **Tables** tab and then select the **USERS** table. You can also set the `auto.offset.reset=earliest`. Like above, if you prefer to construct the statement on your own, make sure it looks like the following. 

```sql
SELECT * FROM USERS EMIT CHANGES;
```

 * You should see the following data in the messages output.

<div align="center">
    <img src="images/users-table-select-results.png" width=75% height=75%>
</div>

> **Note:** Note: If the output does not show up immediately, you may have done everything correctly and it just needs a moment. Setting `auto.offset.reset=earliest` also helps output data faster since the messages are already in the topics.

9. Stop the query by clicking **Stop**. 

***

## <a name="step-8"></a>Create a Persistent Query

A *Persistent Query* runs indefinitely as it processes rows of events and writes to a new topic. You can create persistent queries by deriving new streams and new tables from existing streams or tables.

1. Create a **Persistent Query** named **stocks_enriched** by left joining the stream (**STOCKS_STREAM**) and table (**USERS**). Navigate to the **Editor** and paste the following command.

```sql
CREATE STREAM stocks_enriched AS
    SELECT users.userid AS userid, 
           regionid, 
           gender, 
           side, 
           quantity, 
           symbol, 
           price, 
           account
    FROM stocks_stream
    LEFT JOIN users
    ON stocks_stream.userid = users.userid
EMIT CHANGES;
```

2. Using the **Editor**, query the new stream. You can either type in a select statement or you can navigate to the stream and select the query button, similar to how you did it in a previous step. You can also choose to set `auto.offset.reset=earliest`. Your statement should be the following. 

```sql
SELECT * FROM STOCKS_ENRICHED EMIT CHANGES;
```
* The output from the select statement should be similar to the following: <br> 

<div align="center">
    <img src="images/stocks-enriched-select-results.png" width=75% height=75%>
</div> 

> **Note:** Now that you have a stream of records from the left join of the **USERS** table and **STOCKS_STREAM** stream, you can view the relationship between user and trades in real-time.

4. Next, view the topic created when you created the persistent query with the left join. Navigate to the **Topics** tab on the left hand menu and then select the topic prefixed with a unique ID followed by **STOCKS_ENRICHED**. It should resemble **pksqlc-xxxxxSTOCKS_ENRICHED**. 

<div align="center">
    <img src="images/stocks-enriched-topic.png" width=75% height=75%>
</div>

5. Navigate to **Consumers** on the left hand menu and find the group that corresponds with your **STOCKS_ENRICHED** stream. See the screenshot below as an example. This view shows how well your persistent query is keeping up with the incoming data. You can monitor the consumer lag, current and end offsets, and which topics it is consuming from.

<div align="center">
    <img src="images/ksql-consumer.png" width=75% height=75%>
</div>

***

## <a name="step-9"></a>Aggregate Data

ksqlDB supports several aggregate functions, like `COUNT` and `SUM`, and you can use these to build stateful aggregates on streaming data. In this step, you will walk through some key examples on different ways you can aggregate your data.

1. First, aggregate the data by counting buys and sells of stocks. Navigate back to the Editor and paste the following query to create a new table named **number_of_times_stock_bought**.

```sql
CREATE TABLE number_of_times_stock_bought AS
    SELECT SYMBOL,
           COUNT(QUANTITY) AS total_times_bought
    FROM STOCKS_STREAM
    WHERE side = 'BUY'
    GROUP BY SYMBOL
EMIT CHANGES;
```
2. Next, query this table by going to the **Tables** tab and selecting the query option or typing it directly into the **Editor**. You can also choose to set `auto.offset.reset=earliest`. If you write the statement yourself, make sure it looks like the following.

```sql
SELECT * FROM NUMBER_OF_TIMES_STOCK_BOUGHT EMIT CHANGES; 
```

* The results should look something like the following.

<div align="center">
    <img src="images/times-bought-select-results.png" width=75% height=75%>
</div>

3. Next, create a table that calculates the total number of stocks purchased per symbol. You can choose to set `auto.offset.reset=earliest`.

```sql
CREATE TABLE total_stock_purchased AS
    SELECT symbol,
           SUM(QUANTITY) AS TOTAL_QUANTITY
    FROM STOCKS_ENRICHED
    WHERE SIDE = 'BUY'
    GROUP BY SYMBOL;
```
* Running this query should return something that looks similar to the following.

<div align="center">
    <img src="images/total-bought-select-results.png" width=75% height=75%>
</div>

***

## <a name="step-10"></a> Windowing Operations and Fraud Detection

You will walk through a few examples on how to use ksqlDB for Windowing, including how to use it for anomaly or fraud detection. ksqlDB enables aggregation operations on streams and tables, as you saw in the previous step, and you have the ability to set time boundaries named windows. A window has a start time and an end time, which you access in your queries by using `WINDOWSTART` and `WINDOWEND`. When using Windowing, aggregate functions are applied only to the records that occur within the specified time window. ksqlDB tracks windows per record key.

There are a few different Windowing operations you can use with ksqlDB. You can learn more about them [here](https://docs.ksqldb.io/en/latest/concepts/time-and-windows-in-ksqldb-queries/#window-types).

1. In the ksqlDB **Editor**, paste the following command in order to create a windowed table named **stocks_purchased_today** from the **stocks_topic**. You can set the size of the window to any duration. Set it to 5 minutes in this example.

```sql
CREATE TABLE stocks_purchased_today AS
    SELECT symbol,
           COUNT(*) AS quantity
    FROM stocks_enriched
    WINDOW TUMBLING (SIZE 5 MINUTES)
    GROUP BY symbol;
```

2. Once you have created the windowed table, use the **Editor** or the **Tables** tab to query the table. If you construct the statement on your own, make sure it looks like the following. 

```sql
SELECT * FROM STOCKS_PURCHASED_TODAY EMIT CHANGES;
```

* The output should be similar to the following.

<div align="center">
    <img src="images/today-bought-select-results.png" width=75% height=75%>
</div>

3. Going along with the theme of fraud detection, create a table named **accounts_to_monitor** with accounts to monitor based on their activity during a given time frame. In the ksqlDB **Editor**, paste the following statement and run the query.

```sql
CREATE TABLE accounts_to_monitor AS
    SELECT TIMESTAMPTOSTRING(WINDOWSTART, 'yyyy-MM-dd HH:mm:ss Z') AS WINDOW_START,
           TIMESTAMPTOSTRING(WINDOWEND, 'yyyy-MM-dd HH:mm:ss Z') AS WINDOW_END,
           ACCOUNT,
           COUNT(*) AS quantity
    FROM STOCKS_ENRICHED
    WINDOW TUMBLING (SIZE 5 MINUTES)
    GROUP BY ACCOUNT
    HAVING COUNT(*) > 10;
```

4. Once you have created the **ACCOUNTS_TO_MONITOR** table, use either the **Editor** or the **Tables** tab to query the data from the table. If you construct the statement on your own, make sure it looks like the following.

```sql
SELECT * FROM ACCOUNTS_TO_MONITOR EMIT CHANGES;
```

* The output from this query should look like the following. 

<div align="center">
    <img src="images/accounts-to-monitor-select-results.png" width=75% height=75%>
</div>

***

## <a name="step-11"></a>Pull Queries

Building on our Fraud Detection example from the last step, let’s say our fraud service wants to check on high frequency accounts. The fraud service can send a pull query via the ksql API, today we will just mock it with the UI. Then we can monitor the activity for a suspicious account. 

1. First we need to add a property to our query. Pull queries only filter by the primary key by default. To filter by other fields, we need to enable table scans. You can add a property under the auto.offset.reset one already included. You will need to set ksql.query.pull.table.scan.enabled to true

<div align="center">
    <img src="images/table-scan-true.png" width=50% height=50%>
</div>

2. Now let’s run our pull query in the Editor to see how our accounts are behaving.  

```sql
SELECT * FROM ACCOUNTS_TO_MONITOR
     WHERE QUANTITY > 100;
```
3. Once we have identified a potential troublemaker, we can create an ephemeral push query to monitor future trades from our **STOCKS_ENRICHED** stream. This will continue to push trades to the fraud service for further analysis until it is stopped. 

```sql
SELECT * FROM STOCKS_ENRICHED 
    WHERE ACCOUNT = 'ABC123'
    EMIT CHANGES;
```
***

## <a name="step-12"></a>**Enable Schema Registry**

A topic contains messages, and each message is a key-value pair. The message key or the message value (or both) can be serialized as JSON, Avro, or Protobuf. A schema defines the structure of the data format. 

Confluent Cloud Schema Registry is used to manage schemas and it defines a scope in which schemas can evolve. It stores a versioned history of all schemas, provides multiple compatibility settings, and allows schemas to evolve according to these compatibility settings. It is also fully-managed.

You will be exploring Confluent Cloud Schema Registry in more detail towards the end of the workshop. First, you will need to enable Schema Registry within your environment.

1. Return to your environment by clicking on the Confluent icon at the top left corner and then clicking your environment tile.
  <div align="center">
      <img src="images/sr-cluster.png" width=75% height=75%>
  </div>

2. Click on **Schema Registry**. Select your cloud provider and region, and then click on **Enable Schema Registry**.
  <div align="center">
      <img src="images/sr-tab.png" width=75% height=75%>
  </div>

3. Next, you will create an API Key for Schema Registry. From here, click on the Edit icon under **API credentials**.
4. Click on **Add key** and save your API key and secret - you will also need these during the workshop. Click on **Done**.
5. **Important**: Make note of the **API endpoint**. You will use this endpoint in one of the steps later in the workshop.

## <a name="step-13"></a>**End-to-End cloud ETL deployment, built for 100% cloud services**


Let’s say you have a database such as RDS, or object storage such as AWS S3, or a data warehouse such as Redshift. How do you connect these data systems to your architecture?

There are 2 options: <br>

1. Develop your own connectors using the Kafka Connect framework (this requires a lot of development time and effort).  
2. You can leverage the 200+ connectors Confluent offers out-of-the-box which allows you to configure your sources and sinks in a few, simple steps. To view the complete list of connectors that Confluent offers, please see [Confluent Hub](https://www.confluent.io/hub/).

With Confluent’s connectors, your data systems can communicate with your services, completing your data pipeline. 

If you want to run a connector not yet available as fully-managed in Confluent Cloud, you may run it yourself in a self-managed Connect cluster and connect it to Confluent Cloud. Please note that Confluent will still support any self managed components. 

Now that you have completed setting up your Confluent Cloud account, cluster, topic, and Schema Registry, this next step will guide you how to build end to end pipelines 

Instruction Available here: https://docs.confluent.io/platform/current/tutorials/examples/cloud-etl/docs/index.html

1. Update the demo.cfg file to reflect export DATA_SOURCE='rds'
2. export AWS_PROFILE=default
3. profile must exist in ~/.aws/credentials


## <a name="step-14"></a>**Create Redshift Sink Connector**

The next step is to sink topic data using the Redshift Sink connector. This connector will data from **SUM_PER_SOURCE**

1. From the Confluent Cloud UI, click on the **Connectors** tab on the navigation menu. Click on the **AWS Redshift Sink** icon.

<div align="center" padding=25px>
    <img src="images/connectors.png" width=75% height=75%>
</div>
<br>

3. Click on **Next**.
4. Before launching the connector, you should see something similar to the following. If everything looks similar, select **Launch**. 

<div align="center" padding=25px>
    <img src="images/redshift-conn.png" width=50% height=50%>
</div>

<div align="center">
    <p style="color:red">STOP HERE FOR PRESENTATION</p>
</div>

## <a name="step-15"></a>**Enable Cluster Linking**

1. First, create a **cluster link** from one cluster to another. A cluster link acts as a persistent bridge between the two clusters. 

```sql
confluent kafka link create my-link --cluster $destination_id \
    --source-cluster-id $source_id \
    --source-bootstrap-server $source_endpoint \
    --source-api-key <api-key> --source-api-secret <api-secret>
```
2. To mirror data across the cluster link, you create mirror topics on your destination cluster.

```sql

confluent kafka mirror create users_topic --cluster $destination_id --link my-link

```


## <a name="step-16"></a>**Monitor Confluent Cloud with Datadog**

Instructions here: https://docs.datadoghq.com/integrations/confluent_cloud/

## <a name="step-17"></a>Clean Up Resources

Deleting the resources you created during this workshop will prevent you from incurring additional charges. 

1. The first item to delete is the ksqlDB application. Select the **Delete** button under **Actions** and enter the **Application Name** to confirm the deletion. 

<div align="center">
    <img src="images/delete-ksqldb.png" width=75% height=75%>
</div>

2. Next, delete the Datagen Source connectors for **users** and **stocks**. Navigate to the **Connectors** tab and select each connector. In the top right corner, you will see a **trash** icon. Click the icon and enter the **Connector Name**. Delete both the **users** and **stocks** connectors. 

<div align="center">
    <img src="images/delete-connectors.png" width=75% height=75%>
</div>

3. Finally, under **Cluster Settings**, select the **Delete Cluster** button at the bottom. Enter the **Cluster Name** and select **Confirm**. 

<div align="center">
    <img src="images/delete-cluster.png" width=50% height=50%>
</div>

*** 

## <a name="step-18"></a>Confluent Resources and Further Testing

Here are some links to check out if you are interested in further testing:
- [ksqlDB Tutorials](https://kafka-tutorials.confluent.io/)
- [ksqlDB: The Event Streaming Database, Purpose-Build for Stream Processing](https://ksqldb.io/)
- [Streams and Tables in Apache Kafka: A Primer](https://www.confluent.io/blog/kafka-streams-tables-part-1-event-streaming/)
- [Confluent Cloud Documentation](https://docs.confluent.io/cloud/current/overview.html)
- [Best Practices for Developing Apache Kafka Applications on Confluent Cloud](https://assets.confluent.io/m/14397e757459a58d/original/20200205-WP-Best_Practices_for_Developing_Apache_Kafka_Applications_on_Confluent_Cloud.pdf)

***

