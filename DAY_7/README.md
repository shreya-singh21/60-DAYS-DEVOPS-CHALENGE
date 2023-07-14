# Simple Storage Service (S3)

Amazon S3 (Simple Storage Service) is a highly scalable and durable cloud storage service provided by Amazon Web Services (AWS). It is designed to store and retrieve large amounts of data from anywhere on the web. S3 offers industry-leading storage infrastructure, with high availability, low latency, and strong data consistency.

S3 allow people to store objects(Files or folder) in the bucket.

Bucket names must have globally unique names

**Feature of S3**
• It is a global service

• Low latency and high throughput performance

• It is a Safe place to store your files

• It is object based storage

• Durability: AWS claims Amazon S3 to have a 99.999999999% of durability.
This means the possibility of losing your data stored on S3 is one in a billion.

• A single Amazon S3 object can store maximum of 5 terabytes. The total
volume that an s3 bucket can store is unlimited. If an object size is greater
than 5 gigabytes, you should consider multipart upload.

• S3 Bucket Names must be unique globally

• Lifecycle Management

• Versioning

• Encryption

• Secure Your data using Access Control lists & Bucket Policy

• Many AWS Services uses S3 as an Integration as Well

**S3 - Restrictions and Limitations**

• Bucket ownership is not transferable to another account.

• When we create a bucket, we choose its name and the AWS Region to create it in. After we create a bucket, we can't change its name or Region.

**Let's see how you can create bucket**

1. Go to service S3.

2. Give the name of the bucket.

3. Select region where you need to create bucket.

4. Enabled ACL

5. Give the public access to the bucket.

6. Click on create bucket.

So you have created the bucket

7. Now, you need to upload object. Click on bucket . Upload files into it. 

8. While uploading object below you will find "permission" option. Click on Permission. Click on Grant Public Read Access. 

**To access these objects of bucket**

Click on the name of object. Under properties tab you will find Object URL. Copy URL and paste it on browser.

You will able to access object from browser. Anyone can access this object with URL because you have given public access to the bucket as well as object.

**To Delete Bucket**
1. Delete Object in the bucket.

2. Delete bucket.


**Let's move to the S3 features**

**1. VERSIONING**

Versioning in Amazon s3 is keeping multiple varients of object in same bucket.

It is used to protect against accidental data/object deletion or overwrites.

Versioning can be used for data rentention and archive.

Versioning applies to all object in a bucket not partially applied.

**Advantages of Versioning**

• We can recover deleted object.

• We can maintain different versions of the file.

**Let's see how versioning works!!**

1. Go to s3. Give bucket name.

2. Enabled ACL.

3. Give public access. 

4. Create bucket.

5. Upload txt file in the bucket. Paste the object URL in the browser.

6. Now go to properties tab and enable versioning.

7. Now go to object tab and you will find "show version" button.

8. In the notepad file do some changes.

9. Re- upload the same txt file with some changes and grant public permission. Paste the object URL in the browser. You will Find the new update file.

10. Go to objects. Click on "show version". You will find pervious version file as well as current version file. A tree like structure you will get.

**Advantage** - We can maintain different version of file.

**To recover deleted files**

1. Delete the object.

2. Go to object section and in "show cersion" section you will find a delete marker has been created on the deleted bucket.

3. If you again delete "delete marker" object then you can recover the deleted object.


**2. STATIC WEBSITE HOSTING**

Static website is simple type of website like a normal website where don't have images.Ex- terms and condition website.

1. Go to S3. Create bucket.

2. Give bucket name like www.ramabc.com 

3. Enable ACL.

4. Give public access.

5. Create Bucket.

6. Open bucket and go to Properties tab.

7. Go to "Static Website Hosting". Eanble it.

8. To create this static website, index.html page is mandatory.<br/>
   index.html is home page of website.<br/>
   You can give any name to index document it is not manadatory to only give index.html

9. Save changes

10. Now you have enable the static website hosting.

11. Create Webpage with name index.html and upload the webpage in the bucket.

12. Paste the url in the browser. You will find you static website.


**3. STORAGE CLASSES**

Amazon S3 offers a range of storage classes designed for different use cases. When we upload our data into the bucket then we can select different classes as per our requirement.

Whenever you are uploading objects by default we are alaways selecting storage class.

With the help of storage class we can save the cost like if we have object which is not our use of so we can move the object to different storage class and we can save money.

**Different Types of Storage Classes in S3**

• S3 Standard

• S3 Intelligent-Tiering

• S3 Standard- Infrequent Access

• S3 One Zone- Infrequent Access

• S3 Glacier

• S3 Glacier Deep Archive

**Note** - In real time if thousands of objects are there so it is not possible to change storage class manually.<br/>
           Their is also an automatic way to change storage class.

**How AWS is charging cost for Storage**

There are two ways by which AWS is charging cost for Storage.

1. For storing the object AWS is charging.

2. For Accessing the particular object.


**Storage Classes - S3 Standard**
S3 Standard storage class is used when you have to access object frequently. It offers high durability, availability, and performance object storage for frequently accessed data.

**Key Features:**

• It is default Storage Class, if none specified during upload

• Low latency and high throughput performance

• It designed for 99.99% availability and 99.999999999% durability

• Data is stored in Multi- Availability Zone.

• Use Cases: S3 Standard is appropriate for a wide variety of use cases, including cloud applications, dynamic websites, content distribution, mobile and gaming applications, and big data analytics


**Storage Classes - S3 Intelligent-Tiering**

S3 Intelligent-Tiering is the only cloud storage class that delivers automatic storage cost savings when data access patterns change, without performance impact or operational overhead. S3 Intelligent-Tiering works by storing objects in access tiers: two low latency access tiers optimized for frequent and infrequent access.

**Key Features:**

• S3 Intelligent Tiering storage class is designed to optimize storage costs by automatically moving data to the most cost-effective storage access tier, without performance impact or operational overhead.

• Automatically optimizes storage costs for data with changing access patterns

• It provides low latency and high throughput performance.

• It designed for 99.99% availability and 99.999999999% durability

• Data is stored in Multi- Availability Zone.

• No additional fees apply when objects are moved between access tiers

• S3 monitors access patterns of the objects and moves objects that have not been accessed for 30 consecutive days to the infrequent access tier.

• If the objects are accessed later, S3 Intelligent-Tiering moves the objects back 
to the Frequent Access tier.


**Storage Classes - Standard- Infrequent Access**

S3 Standard-IA is for data that is accessed less frequently,but requires rapid access when needed.

**Key Features:**

• Standard IA storage class is used when data is accessed less frequently but requires rapid access when needed.

• It has a lower fee than S3, but you will be charged for a retrieval fee.

• Suitable for objects greater than 128 KB (smaller objects are charged for 128 KB only) kept for at least 30 days (charged for a minimum of 30 days)

• It designed for 99.99% availability and 99.999999999% durability

• Data is tored in Multi- Availability Zone.

• Use Cases: As a Store for Disaster recovery, backup …


**Storage Classes - One Zone- Infrequent Access**

S3 One Zone-IA is for data that is accessed less frequently, but requires rapid access when needed. Unlike other S3 Storage Classes which store data in a minimum of three Availability Zones (AZs), S3 One Zone-IA stores data in a single AZ and costs 20% less than S3 Standard-IA.

**Key Features:**

S3 one zone-infrequent access storage class is used when data is accessed less frequently but requires rapid access when needed.

• It is an optimal choice for the less frequently accessed data but does not require the availability of Standard or Standard IA storage class.

• It designed for 99.5% availability and 99.999999999% durability of objects in a single availability zone.

• Suitable for objects greater than 128 KB (smaller objects are charged for 128 KB only) kept for at least 30 days (charged for a minimum of 30 days)

• S3 Lifecycle management for automatic migration of objects to other S3 Storage Classes

• The data can be lost at the time of the destruction of an availability zone as it stores the data in a single availability zone.

Use Cases: Storing Secondary backup copies of on premise data or storing data you 
can recreate.


**Storage Classes - S3 Glacier**

S3 Glacier is a secure, durable, and low-cost storage class for data archiving.

**Key Features:**

• S3 Glacier storage class is the cheapest storage class, but it can be used for archive only.

• We can store any amount of data at a lower cost than other storage classes.

• We can upload the objects directly to the S3 Glacier.

• Suitable for objects greater than 40 KB (smaller objects are charged for 40 KB only) kept for at least 90 days (charged for a minimum of 90 days)

• It is designed for 99.999% durability of objects across multiple availability zones.

• Data is tored in Multi- Availability Zone.


**Storage Classes - S3 Glacier Deep Archive**

Glacier Deep Archive storage class provides the lowest-cost data 
archiving where data access is infrequent and retrieval time of hours is acceptable.

**Key Features:**

• Suitable for objects greater than 40 KB (smaller objects are charged for 40 KB only) kept for at least 180 days (charged for a minimum of 180 days)

• Lowest cost storage class designed for long-term retention of data that will be retained for 7-10 years.

• Retrieval time within 12 hours

• It is designed for 99.99999% durability of objects across multiple availability zones.

• Supports long-term retention and digital preservation for data that may be accessed once or twice a year.

Use Cases: Financial Services, Healthcare, and Public Sectors.


**How we can enable storage classes on object**

1. Go to S3. Create bucket.

2. Give the name of bucket.

3. Enable ACL.

4. Grant public access.

5. In the properties section you will find storage classes. By default S3 Standard will be selected.

6. Create bucket. Upload object.

7. Now if you want to change the storage class of object.<br/>
   Go to object<br/>
   Go to properties tab<br/>
   Go to storage class<br/>
   Edit and select whichever you want to choose.


This is How manually we can change the storage classes of object.<br/>
But in Real time we use an automatic way to change storage classes with the help of Life Cycle Management.


**REPLICATION**

Replication is used when you are uploading object in source bucket and it is automatically going to transferred in destination bucket. Replication is like copy whaterver you are uploading in source bucket will reflect in destination bucket.

**There are two types of Replication**

1. Cross Region Replication - In this source and destination will be in different region.

2. Same region Replication - In this source and destination will be in same region.

**REplication - Same Region**

1. Create two buckets in same region.

2. Enable ACL in both buckets.

3. Give public access.

4. Enable Bucket Versioning in both the buckets. It is the manadatory step for replication.

5. Create both buckets.

6. Click on First Bucket. Go to Management tab. 

7. In the replication section create replication rules.

8. Select Destination bucket<br/>
   In destination you can choose a bucket in the same account or you can choose bucket in another account.<br/>
   If you are choosing another account then you have to provide Account ID of that person's account.

9. create replication.

10. Upload one object in source bucket.

11. After few minutues you will see the same object get reflected in the destination bucket.















