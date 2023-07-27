## DATABASE


**Why companies want to store data?**

ompanies store data for various reasons, and data has become a valuable asset in the modern business landscape. Here are some key reasons why companies want to store data:

1. **Business Intelligence and Analytics**: Data is essential for gaining insights into business operations, customer behavior, market trends, and other critical aspects. By analyzing data, companies can make informed decisions, identify opportunities, and optimize their strategies.

2. **Customer Understanding**: Data helps companies understand their customers better. By collecting and analyzing customer data, businesses can personalize their products, services, and marketing efforts to meet individual preferences and needs.

3. **Improving Products and Services**: Storing data allows companies to track product performance, gather feedback from customers, and identify areas for improvement. This data-driven approach helps in developing better products and services.

4. **Disaster Recovery and Business Continuity**: Storing data in secure and redundant environments ensures that companies can recover their operations in the event of a disaster or system failure.


**Why there is need of Database when we can use excel to store data?**

While Excel is a useful tool for handling small amounts of data and performing basic calculations, it is not designed to handle the complex and large-scale data requirements of modern businesses. There are several reasons why there is a need for databases over Excel for certain use cases:

1. Databases are designed to handle vast amounts of data and can scale to accommodate the growing data needs of businesses. Excel, on the other hand, has limitations in terms of the amount of data it can handle efficiently.

2. Databases are optimized for data retrieval, storage, and manipulation. They use indexing, caching, and other techniques to ensure fast and efficient access to data. Excel may become slow and unresponsive when dealing with large datasets.

3. Databases support concurrent access by multiple users, allowing teams to collaborate on data simultaneously. Excel files, especially when stored on shared drives, can lead to conflicts and version control issues when multiple users try to modify the same file simultaneously.

4. Databases offer backup and recovery mechanisms to protect against data loss. Excel files are susceptible to accidental deletion or corruption without a robust backup strategy.


**What is database?**

In Amazon Web Services (AWS), a database is a managed and scalable service that allows you to store and manage data efficiently in the cloud.

Databases play a crucial role in the functioning of an application. Also, performance of an application is directly dependent on how the underlying database performs for the application.

There are numerous options we can find to run the managed relational data and also the managed NoSQL databases.


**AWS DATABASE - ADVANTAGES**

• Highly Scalable: We can scale your database as our application grows without any downtime!

• Fully Managed: Everything, from maintenance to hardware upgrades, is managed by AWS.

• Enterprise Class: We get the same world-class infrastructure used by Amazon’s giant ecommerce platform.

• Workforce Reduction: Since everything is managed by AWS, you don’t need a Database Maintenance team in your organization.


**AWS DATABASE - TYPES**

• Relational Database

• Key Value

• In Memory

• Document

• Wide Column

• Graph

• Time Series

• Ledger


**What is NoSql Database?**

The term "NoSQL" stands for "Not Only SQL," indicating that these databases can handle data beyond the structured format used in SQL-based relational databases. 

Here we don't need SQL knowlwdge.


**AWS DATABASE - KEY VALUE**

A key-value database is a type of non-relational database that uses a simple key-value method to store data. A key-value database stores data as a collection of key-value pairs in which a key serves as a unique identifier. It is NoSQL Database.

**Use Cases**: High-traffic web applications, ecommerce systems, gaming applications.

**Types of AWS Services in Key Values**<br/>
Amazon DynamoDB


**AWS DATABASE - IN MEMORY**

An in-memory database keeps all its data in the random access memory (RAM) of a computer. Only the main memory is accessed when querying data. This allows for faster access of that data than a disk-based system. It is NoSQL Database.

**User Cases**: Session management, gaming leaderboards, real time Bidding.

**Types of AWS Services in In Memory**<br/>
Amazon ElastiCache<br/>
Amazon MemoryDB for Redis


**AWS DATABASE - DOCUMENT**

Document databases store data in JSON or JSON-like documents. You can query data using the same document-model format used in programming applications.

**User Cases**: Content management, catalogs, user profiles

**Types of AWS Services in Document**<br/>
Amazon DocumentDB (with MongoDB compatibility)


**AWS DATABASE - WIDE COLUMN**

In Wide Column data is stored and grouped into separately stored columns instead of rows. Queries for a particular value in a column are very fast, as the entire column can be loaded and searched quickly. Such databases organize information into columns that function similarly to tables in relational databases.

**Use Cases**: High-scale industrial apps for equipment maintenance, fleet management, and route optimization

**Types of AWS Services in Wide Column**<br/>
Amazon Keyspaces


**AWS DATABASE - GRAPH**

This database type represents relationships directly. You can query data with specific graph languages. It storing billions of relationships and querying the graph with milliseconds latency.

**Use Cases**: Fraud detection, social networking, and recommendation engines

**Types of AWS Services in Graph**<br/>
Amazon Neptune


**AWS DATABASE - TIME SERIES**

Time-series databases store data in time-order and as append-only. We can query data over various time intervals. Time series data are simply measurements or events that are tracked, monitored, down sampled, and aggregated over time.

**Use Cases**: Application performance monitoring, trades in a market, sensor data, DevOps, network data & many other types of analytics data.

**Types of AWS Services in Time Series**<br/>
Amazon Timestream


**AWS DATABASE - LEDGER**

Ledger databases add a layer of digital signatures for each transaction so anyone can audit the list and see that it was constructed correctly. More importantly, no one has gone back to adjust a previous transaction to change history.

**Use Cases**: Banking Transactions, supply chain, Crypto currency, Insurance claims & HR and payroll

**Types of AWS Services in Ledger**<br/>
Amazon Quantum Ledger Database


**AWS DATABASE - RELATIONAL DATABASE**

A relational database is a type of database management system (DBMS) that stores and organizes data in a tabular format, consisting of rows and columns. It uses a structured approach where data is stored in related tables, and the relationships between the tables are defined by keys. Tables are used to hold information about the objects to be represented in the database.
Eachcolumn in a table holds a certain kind of data and afield stores the actual value of an attribute. The rows in table represent a collection of related values of one object or entity. Each row in a table could be marked with a unique identifier called a primary key,and rows among multiple tables can be made related using foreign keys.

**Use Cases**: Traditional applications, enterprise resource planning (ERP), customer relationship management (CRM), and ecommerce

**Types of AWS Services in Relational Database**<br/>
RDS (Relational Database Service)<br/>
Amazon Redshift


**Amazon RDS supports six DB engine types:**
• Amazon Aurora<br/>
• Oracle<br/>
• Microsoft SQL Server<br/>
• MySQL<br/>
• PostgreSQL<br/>
• MariaDB<br/>


## RELATIONAL DATABASE SERVICE - RDS

Amazon RDS supports an array of database engines to store and organize data. It also helps with relational database management tasks, such as data migration, backup, recovery and patching.

**Advantage of RDS**

• Automatic Backups<br/>
• Multi Availability Zone<br/>
• Read Replica<br/>

**RDS - BACKUP**

Backup refers to the copying of physical or databases to a secondary location for preservation in case of equipment failure.

**Types of Backups**
Automatic Backup<br/>
Manual Backup<br/>


**AUTOMATIC BACKUP**

•Automatic backup is a type of data backup model that requires little or no human intervention in backing up and storing data from a local network/system to a backup facility.

• Automating the backup process saves time and complexity required to manually back up a computer, network or IT environment.

• Automatic backup allow us to recover our database to any point in time within a retention period. The retention period can be between 1 and 35 days.

• Default Retention Period is 7 Days

• Automatic backups will take a full daily snapshot and will also store transaction logs throughout the day. When we do a recovery, AWS will first choose the most recent daily backup, and then apply transaction logs relevant to that day.

• After they are deleted, the automated backups can't berecovered.

• Automatic backups are enabled by default


**AUTOMATIC BACKUP RULE**

Our DB instance must be in the AVAILABLE state for automated backups to occur. Automated backups don't occur while your DB instance is in a state other than AVAILABLE, for example STORAGE_FULL.


**MANUAL BACKUP**

• Manual Backup are also called as Snapshot.

• Database Snapshot are done manually. They are stored even after we delete the original RDS instance, unlike automatically backups.

• We can have up to 100 manual snapshots per Region.


**RDS - MULTI AVAILABILITY ZONE**

If we wre enable this option we need to pay some additional cost to aws.<br/>
Multi Availability Zone will create replica of database in another region. If my primary databse is down then AWS will redirect our customer automatically to secondary database. With the help of this our customer will not get impacted. Without any downtime it will automatically switch to secondary database.

• Multi AZ allow us to have an exact copy of our production database in another AZ. AWS handles the replication for us. When our production database is written to, this write will automatically be synchronized to the stand by database.

• In the event of planned database maintenance, database instance failure or and Availability zone failure, Amazon RDS will automatically failover to the standby so that database operations can resume quickly without administrative intervention.

• Both Database Servers have same DNS endpoints


**RDS - READ REPLICA**

• Read replica allows us to have a read only copy of our production database.

Example - We have primary database. In main database we can read data as well as write data. If you give this primary database to everyone so anyone can delete anuthing, insert anything. Anyone can do anything with data.So we do not give primary database access to everyone. To avoid this situation we can give read replica of our database so that they can only read your data.

• Amazon RDS Read Replicas provide enhanced performance and durability for RDS database (DB) instances.

• They make it easy to elastically scale out beyond the capacity constraints of a single DB instance for read-heavy database workloads.

• We can have up to 5 read replica copies of any database.    

• We can have read replicas of read replicas (But Latency will be there)

• When we create a read replica, RDS gives us a read-only endpoint which is a DNS that resolves only to our read replica.

• A read replica and the master may be in different availability zones, and even in different regions.



**Let's start creation of RDS**

1. Go to RDS Service.

2. Click on create database.

3. Select standard create as database creation method

4. Below down will get six type of RDS<br/>
   • Amazon Aurora<br/>
   • Oracle<br/>
   • Microsoft SQL Server<br/>
   • MySQL<br/>
   • PostgreSQL<br/>
   • MariaDB<br/>
   
5. Select MySQL

6. In template will get<br/>
   Production <br/>
   Dev/Test<br/>
   Free Tier<br/>

7. Select free tier

8. Enter the database name

9. Enter Master password & confirm password

10. Select type of instance - t2.micro

11. Allocate storage for database

12. Click on Enable storage autosacaling. It will automativally increased the size of database when there is need.

13. Go to Connectivity

14. Select default VPC & Select default subnet group

15. Select Yes for Public Access

16. Select Create new for Security group & enter the name for security group

17. Select availability Zone

18. Click on Create database

19. When it get ready it will take automatc backup.

20. Download MYSQL Workbench. It is a tool whwre we can execute our SQL queries

21. We will connect database with Mysql workbench

22. Open MYSQL Workbench

23. Click on Database 

24. Click on Manage connection

25. Give connection name

26. Give the hostname(endpoint)
    To get the endpoint
    Go to database
    Click on database
    Below down will get endpoint
    paste the endpoint to the hostname

27. Enter username - admin

28. Click on store in vault

29. Enter password

30. Click on ok

31. Again go to database

32. Click on connect to database

33. Click ok

34. We can type command - show database<br/>
    It will show all existing databases

35. We can run any SQL queries


**RDS - READ REPLICA**

1. Select database. Click on Action.

2. Click on create read replica

3. Select type of instance

4. We can allocate storage

5. We can give destination region

6. Select default security group

7. We can enable delete protection so in real time can delete this data.

8. Click on read replica

**Note** - Read Replica is chargable.


**RDS - MANUAL SNAPSHOT**

1. Select database. Click on Action.

2. Click on take snapshot

**Note** - Manual snapshot is chargable.


**RDS - RESTORE SNAPSHOT**

1. If we have snapshot then select the particular snapshot.

2. Click on Action and restore snapshot


**RDS - RESTORE BACKUP**

1. Select automatic backup.

2. Go to Action and click on restore to point in time.


**RDS - ENABLE MULTI AVAILABILITY ZONE**

1. Select database

2. Click on modify

3. Go to Availability & Durability

4. Select create a standby instance


## KEY VALUE DATABASE - DYNAMO DB

Amazon DynamoDB is a fast, fully-managed NoSQL database service that makes it simple and costeffective to store and retrieve any amount of data, and serve any level of request traffic.


**Features of DynamoDB**

DynamoDB Has Two Constraints<br/>
Primary Key (Partition Key)<br/>
Composite Primary Key (Sort Key)<br/>


**PRIMARY KEY(PARTITION KEY)**

In classes we give unique roll number to  every students no one will get same roll number<br/>
rollno -> student name<br/>
This unique roll no will be our Partition key where we can only enter the unique values. If we give duplicate values then system will show error message.<br/>
In partition key we have unique features.

There is also other feature of primary key is not null. If we give student name and not give the roll number then it will show error.

When I apply partition key we cannot enter duplicate values and we cannot give null.Always need to enter unique values.


**COMPOSITE KEY(SORT KEY)**

Sort key is apply on multiple column. In this If we have two column like Branch code and Account Number and we have given 1234 as Branch code and 5678 as Account Number. In next entry we can give same 1234 as Branch code but need to give another Account number like 9012. In this we can enter duplicate value but only in one column. 


**Let's create DynamoDb database**

1. Go to DynamoDB 

2. Click on Create table

3. Enter the table Name

4. Enter Partition Key

5. Enter Sort Key

6. Click on create table.

7. Click on table name

8. Click on Explore table items

9. Now we have to create item. Click on Create item

10. Enter the value

11. By default in aws we have two column but we can get more numbers of column nad also can set attribute. Click on Add New Attributes for more columns

12. Select type as string

13. Enter the attribute name & value

14. Click on Create Item

**Note** - In this we can give duplicate values only in one column. We cannot give duplicate values in both column.<br/>
           Also we can not leave column as blank. It will throw error message.



























