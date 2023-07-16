# Day 7:  Simple Storage Service (S3)

Amazon S3 (Simple Storage Service) is a highly scalable and durable cloud storage service provided by Amazon Web Services (AWS). It offers a versatile solution for storing and retrieving large amounts of data from anywhere on the web. Unlike other AWS storage types, such as EBS and EFS, S3 is specifically designed for object-based storage, making it suitable for a wide range of use cases. It stands out from other AWS storage types due to its unique characteristics and use cases.

## How S3 Differs from Other AWS Storage Types

S3 provides several distinct advantages compared to other AWS storage types:

1. Object-Based Storage: Unlike EBS and EFS, which provide block-level and file-level storage respectively, S3 offers object-based storage. This means that data is stored as individual objects (files) within buckets, making S3 a versatile solution for storing and retrieving unstructured data like files, images, videos, and documents.

2. Global Service: S3 is a global service available in multiple AWS regions worldwide. It provides the ability to store and access data from anywhere on the web with low latency and high throughput performance. In contrast, EBS volumes are attached to specific EC2 instances in a single availability zone, while EFS file systems are associated with a specific region.

3. Durability and Scalability: S3 is designed for durability, boasting a 99.999999999% durability rating. This means that the probability of losing data stored in S3 is exceptionally low. Additionally, S3 offers virtually unlimited storage capacity, allowing you to scale your storage needs without limitations. In comparison, EBS volumes and EFS file systems have specific size limits and scalability considerations.

4. Use Cases: S3 is ideal for storing and retrieving large amounts of data, making it suitable for various use cases such as backup and restore, data archiving, content distribution, data lakes, and web hosting. EBS, on the other hand, is primarily used as block-level storage for EC2 instances, providing persistent storage for applications and databases. EFS is a fully managed file storage service that is optimized for shared access across multiple EC2 instances, making it suitable for scenarios requiring concurrent access to files.

## Key Features of S3

- Global Service: S3 is available in multiple AWS regions worldwide, allowing you to store and access your data globally with low latency and high throughput performance.

- Safe Data Storage: S3 provides a secure and reliable place to store your files, ensuring high durability with a 99.999999999% guarantee of data durability. This means that the probability of losing your data stored in S3 is incredibly low.

- Scalability and Flexibility: With S3, you can store an unlimited volume of data in the form of objects. Each object can store up to 5 terabytes of data. If your object size exceeds 5 gigabytes, it is recommended to use multipart upload.

- Lifecycle Management: S3 offers lifecycle management features, allowing you to define rules to automate the transition of objects between storage classes based on their lifecycle stages. This helps optimize storage costs and performance.

- Versioning: S3 supports versioning, which allows you to keep multiple versions of an object. This feature helps protect against accidental deletion or modification of objects and enables easy retrieval of previous versions when needed.

- Encryption: S3 provides encryption options to secure your data at rest. You can choose to encrypt objects using server-side encryption with AWS Key Management Service (KMS) keys or client-side encryption.

- Access Control: S3 offers fine-grained access control through Access Control Lists (ACLs) and Bucket Policies. You can define granular permissions to control who can access your S3 buckets and objects.

- Integration with AWS Services: S3 is integrated with various AWS services, making it a central storage solution for data used by other AWS services like EC2, EMR, and more.

## S3 - Restrictions and Limitations

- Bucket Ownership: The ownership of an S3 bucket is tied to the AWS account that created it and cannot be transferred to another account.

- Bucket Name and Region: When creating an S3 bucket, you choose a unique name and the AWS Region where it will be created. Once created, the bucket name and region cannot be changed.

- Bucket Limit: By default, you can create up to 100 buckets in each of your AWS accounts. If you need additional buckets, you can increase your account bucket limit to a maximum of 1,000 buckets by submitting a service limit increase. It's important to note that there is no difference in performance whether you use many buckets or just a few.

By utilizing Amazon S3, you can benefit from its scalable, durable, and feature-rich storage capabilities, ensuring the security and accessibility of your data. It serves as a reliable solution for a wide range of use cases, from simple file storage to data backups and serving static website content.

# S3 Overview of Buckets

Amazon S3 allows users to store objects, such as files, in containers called "buckets." Here are some key points to know about S3 buckets:

- Buckets are globally unique: Each bucket name must be unique across all existing buckets in the world. This uniqueness ensures that no two users can create buckets with the same name.

- Buckets are defined at the region level: When creating a bucket, you specify the AWS region where it will be stored. This helps in data locality and compliance requirements.

- Naming Convention: When naming your buckets, keep the following guidelines in mind:
  - No Uppercase: Bucket names should be in lowercase letters.
  - No Underscore: Bucket names should not contain underscores.
  - Length: Bucket names can be between 3 and 63 characters long.
  - Not an IP Address: Bucket names cannot be in the format of an IP address like 224.245.278.135.
  - Start with lowercase letter or number: Bucket names should start with a lowercase letter or a number.

By adhering to these naming conventions, you can create unique and well-formed bucket names for your Amazon S3 storage needs.

## Creating an S3 Bucket

To create an S3 bucket, follow these steps:

1. Go to the S3 service in your AWS Management Console.
2. Click on "Create Bucket."
3. Provide a unique name for your bucket.
4. Select the region where you want to create the bucket.
5. Configure the Access Control List (ACL) settings.
6. Choose whether to grant public access to the bucket. If you want to give public access, select the appropriate options; otherwise, keep the bucket private.
7. Click on "Create Bucket" to complete the process.

## Uploading Objects to the Bucket

To upload objects to your S3 bucket, follow these steps:

1. Locate your created bucket and click on its name.
2. Choose the "Upload" option to upload files into the bucket.
3. While uploading the object, you will find the "Permission" option.
4. Click on "Permission" and select "Grant Public Read Access" if you want the object to be publicly accessible; otherwise, adjust the permissions accordingly.

By following these steps, you can create an S3 bucket and upload objects with the desired permissions.

## Accessing Objects in the Bucket

To access objects in your S3 bucket, follow these steps:

1. Click on the name of the object you want to access.
2. Under the "Properties" tab, you will find the Object URL.
3. Copy the URL and paste it into your web browser.
4. You will be able to access the object directly from your browser. Keep in mind that anyone with the URL can access the object since you have granted public access to both the bucket and the object.

## Deleting a Bucket

To delete an S3 bucket, follow these steps:

1. Delete all objects within the bucket.
2. Once the bucket is empty, click on the "Delete bucket" option.

By following these steps, you can access objects in your S3 bucket and delete the bucket when needed.

# S3 Pricing

Amazon Simple Storage Service (Amazon S3) offers flexible and transparent pricing options for its object storage service. Understanding the pricing structure can help you effectively manage costs while utilizing the benefits of S3.

## Free Tier and Limited Capacity

Amazon S3 provides a free tier option to help you get started. The free tier includes a limited storage capacity for 12 months. To learn more about the free tier and its limitations, click [here](https://aws.amazon.com/free/).

## Storage Tiers

AWS S3 offers different storage tiers with varying pricing structures. The pricing is based on the amount of storage (per GB per month) and the selected storage tier. Here are some key considerations:

- AWS S3 Standard: This tier provides instant access with low data retrieval costs. However, it has a relatively higher cost per GB. It is suitable for frequently accessed data.

- Lower Cost Tiers: AWS S3 also offers lower cost tiers that provide a lower cost per GB. However, these tiers may have higher costs for data retrieval or delayed data retrieval. They are ideal for less frequently accessed data or long-term storage needs.

## Cost per Requests

In addition to storage costs, AWS S3 has a cost per 1,000 requests, which depends on the type of request made. It's important to consider the request frequency and type to estimate the overall cost accurately.

## Data Transfer Charges

Data transfer from AWS S3 to the internet or to certain AWS regions may incur additional charges. It's essential to be aware of these charges when planning data transfers.

## Management and Analytics

AWS S3 provides additional features for automating the data lifecycle and optimizing storage tiers based on usage patterns. These management and analytics features may come with additional charges. Consider these costs while implementing automation and data optimization strategies.

## Replication

If you set up data replication in AWS S3, it's important to note that data transfer and operations performed during replication are charged like regular AWS S3 operations. Keep this in mind when configuring replication for your storage needs.

By understanding the pricing structure and considering your specific use case, you can effectively manage costs while leveraging the benefits of Amazon S3.

For more detailed information on pricing, including the latest updates and specific pricing details, please refer to the [AWS S3 Pricing](https://aws.amazon.com/s3/pricing/) page.


# S3 Versioning

Versioning in Amazon S3 allows you to keep multiple variants of an object within the same bucket. It serves as a safeguard against accidental data or object deletion or overwrites. Versioning can be used for data retention and archiving purposes. Note that versioning applies to all objects within a bucket and is not selectively applied.

**Advantages of Versioning**

- Recover Deleted Objects: With versioning enabled, you can recover deleted objects. Even if an object is deleted, previous versions are still retained and accessible.

- Maintain Different Versions of Files: Versioning allows you to keep different versions of the same file. Each upload or modification creates a new version, preserving the history of changes made to the object.

**Let's see how versioning works!**

1. Go to the S3 console and select the desired bucket.

2. Configure the Access Control List (ACL) settings for the bucket, including granting public access if required.

3. Create the bucket and upload a text file. Copy the object URL and paste it into your browser to verify its accessibility.

4. Enable versioning for the bucket by navigating to the bucket's properties tab.

5. Access the object tab, where you will find a "Show Versions" button. Click on it to view the different versions of the object.

6. To observe versioning in action, make changes to the text file and re-upload it with modifications. Grant public permission to the new version if desired. Paste the object URL in your browser to access the updated file.

7. Navigate to the object tab and click on "Show Versions" to see a tree-like structure displaying the previous and current versions of the file.

The advantage of versioning is that you can maintain different versions of a file, allowing you to track changes and recover previous versions if needed.

**Recovering Deleted Files**

1. Delete the object.

2. In the object section, under "Show Versions," you will find a delete marker indicating the deletion of the object.

3. If you delete the "delete marker" object, you can recover the previously deleted object.

By utilizing versioning in Amazon S3, you can effectively manage and preserve different versions of your files and recover deleted objects if necessary.


# Static Website Hosting with Amazon S3

This guide will walk you through the process of hosting a static website on Amazon S3. Hosting your website on S3 provides scalability, durability, and cost-effectiveness. Let's get started!

## Getting Started

To host your static website on Amazon S3, follow these steps:

1. Create a new bucket in the Amazon S3 console.
2. Enable ACLs (Access Control Lists) for the bucket to manage permissions.
3. Unblock all public access to allow the website to be publicly accessible.
4. Upload your static website files to the bucket:
   - Make sure the main logic of your website is contained in the `index.html` file. This file serves as the entry point of your website.
   - Create an `error.html` file to handle and display errors encountered during website access.
5. Configure the bucket for static website hosting in the Amazon S3 console.
6. Set the index document and error document for your website.
7. Save the changes and note down the website endpoint URL.

## Testing Your Website

Once you have completed the setup, you can test your static website:

1. Open your browser and enter the website endpoint URL noted earlier.
2. The `index.html` file will be displayed as the main page of your website.
3. To test the error handling, try accessing a non-existent file on your website. You should see the customized error message from the `error.html` file.

Congratulations! You have successfully hosted your static website on Amazon S3.

## Additional Considerations

- To further secure your website, you can configure bucket policies and use HTTPS for encrypted communication.
- If you need to make changes to your website, simply update the files in the bucket, and the changes will be reflected on your website.

Enjoy your scalable and cost-effective static website hosting with Amazon S3!

# STORAGE CLASSES

Amazon S3 offers a range of storage classes designed for different use cases. When we upload our data into the bucket then we can select different classes as per our requirement.

Whenever you are uploading objects by default we are alaways selecting storage class.

With the help of storage class we can save the cost like if we have object which is not our use of so we can move the object to different storage class and we can save money.

## Different Types of Storage Classes in S3

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


### Storage Classes - S3 Standard
S3 Standard storage class is used when you have to access object frequently. It offers high durability, availability, and performance object storage for frequently accessed data.

**Key Features:**

• It is default Storage Class, if none specified during upload

• Low latency and high throughput performance

• It designed for 99.99% availability and 99.999999999% durability

• Data is stored in Multi- Availability Zone.

• Use Cases: S3 Standard is appropriate for a wide variety of use cases, including cloud applications, dynamic websites, content distribution, mobile and gaming applications, and big data analytics


### Storage Classes - S3 Intelligent-Tiering

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


### Storage Classes - Standard- Infrequent Access

S3 Standard-IA is for data that is accessed less frequently,but requires rapid access when needed.

**Key Features:**

• Standard IA storage class is used when data is accessed less frequently but requires rapid access when needed.

• It has a lower fee than S3, but you will be charged for a retrieval fee.

• Suitable for objects greater than 128 KB (smaller objects are charged for 128 KB only) kept for at least 30 days (charged for a minimum of 30 days)

• It designed for 99.99% availability and 99.999999999% durability

• Data is tored in Multi- Availability Zone.

• Use Cases: As a Store for Disaster recovery, backup …


### Storage Classes - One Zone- Infrequent Access

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


### Storage Classes - S3 Glacier

S3 Glacier is a secure, durable, and low-cost storage class for data archiving.

**Key Features:**

• S3 Glacier storage class is the cheapest storage class, but it can be used for archive only.

• We can store any amount of data at a lower cost than other storage classes.

• We can upload the objects directly to the S3 Glacier.

• Suitable for objects greater than 40 KB (smaller objects are charged for 40 KB only) kept for at least 90 days (charged for a minimum of 90 days)

• It is designed for 99.999% durability of objects across multiple availability zones.

• Data is tored in Multi- Availability Zone.


### Storage Classes - S3 Glacier Deep Archive

Glacier Deep Archive storage class provides the lowest-cost data 
archiving where data access is infrequent and retrieval time of hours is acceptable.

**Key Features:**

• Suitable for objects greater than 40 KB (smaller objects are charged for 40 KB only) kept for at least 180 days (charged for a minimum of 180 days)

• Lowest cost storage class designed for long-term retention of data that will be retained for 7-10 years.

• Retrieval time within 12 hours

• It is designed for 99.99999% durability of objects across multiple availability zones.

• Supports long-term retention and digital preservation for data that may be accessed once or twice a year.

Use Cases: Financial Services, Healthcare, and Public Sectors.


### How we can enable storage classes on object

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


# REPLICATION

In AWS, replication refers to the automatic copying of objects from a source bucket to a destination bucket. When we enable replication for a bucket, any object we upload to the source bucket will be automatically replicated and stored in the destination bucket.

Think of replication as creating a backup or replica of your data. It ensures that your objects are securely stored in multiple locations, providing redundancy and helping to protect against data loss. Replication is useful for scenarios such as data backup, disaster recovery, or distributing data across different regions.

For example, let's say we have a source bucket called "Bucket-A" in the US East (Ohio) region, and a destination bucket called "Bucket-B" in the US West (Oregon) region. When we upload an object to "Bucket-A", AWS replication automatically copies that object and stores it in "Bucket-B". Any changes or deletions made to the object in "Bucket-A" will be replicated and reflected in "Bucket-B" as well.

Replication in AWS ensures data durability and availability by maintaining consistent copies of your objects across different regions. It provides an extra layer of protection and helps ensure that your data is accessible even in the event of an outage or failure in one region.

By leveraging replication, you can enhance the resilience and availability of your data, improve disaster recovery capabilities, and ensure business continuity. AWS offers various replication options, allowing you to customize the replication settings based on your specific requirements and use cases.

## There are two types of Replication

1. Cross Region Replication - In this source and destination will be in different region.

2. Same region Replication - In this source and destination will be in same region.

## Replication - Same Region

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

**Note**- In the same region your source bucket got replicated.


## Replication - Cross Region

1. Create two buckets in different region.

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

**Note**- In the different region your source bucket got replicated.


# TRANSFER ACCELERATION

Transfer Acceleration is a feature in Amazon S3 that makes file transfers between your client and an S3 bucket faster, easier, and more secure. It is especially useful when you need to transfer files over long distances. Transfer Acceleration leverages Amazon CloudFront's globally distributed edge locations to optimize transfer speeds.

Let's consider an example to understand how Transfer Acceleration works. Imagine you have an end user in India who wants to upload a large file to an S3 bucket located in the USA region. Due to the long distance between the user and the bucket, the file transfer may be slow, and there could be network fluctuations. If the transfer gets interrupted, the user would need to start the upload again, causing frustration and wasting time.

To overcome this challenge, we can enable Transfer Acceleration for the S3 bucket. This feature utilizes Amazon CloudFront's edge locations, which are distributed globally, including in India. When the end user tries to upload the file, the data is automatically routed to the nearest CloudFront edge location in India. From there, it is quickly transferred to the S3 bucket in the USA region, bypassing the long-distance network route.

By using Transfer Acceleration, the file transfer speed is significantly improved. The data travels through the Amazon CloudFront network, which is optimized for performance and reliability, resulting in faster and more efficient transfers. Additionally, Transfer Acceleration ensures the security and integrity of the data during transit.

In summary, Transfer Acceleration is a valuable feature that enhances file transfer speeds over long distances. It leverages Amazon CloudFront's global edge locations to optimize transfers between clients and S3 buckets. By enabling Transfer Acceleration, you can save time, improve efficiency, and provide a better user experience, especially when transferring large files across regions.

### To enable edge location

1. Craete  S3 bucket.

2. Give name to the bucket.

3. Eanble ACL

4. Give public access

5. Create bucket

6. Click on bucket name.

7. Go to properties tab

8. Click on transfer acceleration button and enable it.

9. save changes.

**Note**- If anyone will upload the object in the bucket then first it will go to nearest edge location then it will transfer to region bucket and all the process will happen within friction of second.

# Metadata and Tags

## Metadata

Metadata is used to provide additional information about the objects uploaded to the bucket. It allows you to attach custom information to your objects, such as object creation date, author, or any other relevant details. There are two types of metadata: system-defined object metadata and user-defined object metadata.

### System-defined object metadata

Every object in a bucket has a set of system metadata that is processed by Amazon S3. Examples of system metadata include object creation date, storage class, and server-side encryption status. These values are controlled by Amazon S3 and cannot be modified by users.

### User-defined object metadata

When uploading an object, you can also assign custom metadata to the object. This optional information is provided as a name-value (key-value) pair when sending a PUT or POST request to create the object. User-defined metadata allows you to add custom tags and labels to your objects to provide more context or categorize them according to your needs.

#### Assigning Metadata

1. Create a bucket.
2. Enable ACLs and provide public access.
3. Upload an object to the bucket.
4. Grant public access to the object.
5. Go to the Properties tab of the object.
6. System-defined metadata is already created by the system.
7. Click on edit for metadata.
8. Select system-defined metadata and choose the desired key-value pair.
9. Select user-defined metadata and enter your custom key-value pair according to your requirements.

## Tags

Tags are used to categorize storage and provide additional information for billing and organizational purposes. With object tagging, you can assign tags to your objects, allowing you to easily track and identify them based on specific criteria or attributes.

### Assigning Tags

1. Click on Edit for tags.
2. Enter the desired key-value pair as per your requirements.
3. Click on save changes.

Tags are useful for organizing and managing objects, especially when dealing with large amounts of data. They help in cost allocation, identifying object purposes, and implementing effective data management strategies.

By utilizing metadata and tags in Amazon S3, you can enhance the organization, classification, and management of your objects, making it easier to search, track, and understand your data.


## ACCESS CONTROL LIST

Access Control List is a feature used to control and manage access to objects and buckets in Amazon S3. It allows you to specify who can access your resources and what level of access they have.

Let's understand ACL with an example. Imagine you have a bucket in Amazon S3 containing important files and you want to grant access to another person who has a different AWS account. By default, the bucket and the objects within it are private and only accessible by the account that created them.

To provide access to the other person, you can use an Access Control List. You have the flexibility to apply ACL at two levels: object level and bucket level.

At the object level, you can specify individual permissions for each object within the bucket. For example, you can allow the other person to read or write specific objects while restricting access to others.

At the bucket level, you can define permissions that apply to all objects within the bucket. This allows you to grant broader access to the entire bucket, making it convenient when sharing multiple objects with the same person or group.

To apply ACL, you will need the Canonical User ID of the person's AWS account. The Canonical User ID is a unique identifier associated with each AWS account. You can find your own Canonical User ID by navigating to your AWS account settings, specifically in the security credentials section.

By specifying the appropriate permissions in the ACL, you can control who can access your bucket and objects and what actions they can perform. This helps ensure the security and confidentiality of your data in Amazon S3.

In summary, Access Control List (ACL) is a feature that allows you to manage access to your Amazon S3 resources. It provides the flexibility to grant permissions at the object level or bucket level, and you can specify different levels of access for different users. By utilizing ACL, you can securely share your resources with other AWS accounts while maintaining control over who can access your data.

**Cronical User ID**<br/>
Click on your username <br/> 
security credentials <br/>
In account details you will find cronical user ID

**ACL at object level**

1. Create s3 bucket

2. Give bucket name

3. Enable ACL

4. Give public access

5. Create bucket

6. Upload object in bucket and give public access to object

7. Click on object. Go to Permission tab

8. Edit ACL. Give cronical ID of other AWS account person for which you want to provide access of your bucket.

**ACL at bucket level**

In this you can give bucket access to other AWS account person.

1. Create s3 bucket

2. Give bucket name

3. Enable ACL

4. Give public access

5. Create bucket

6. Upload object in bucket and give public access to object.

7. click on bucket. Go to Permission tab. 

8. Go to Access control list. Give cronical ID.

9. save changes.


# BUCKET POLICY

Bucket policy in AWS refers to an access policy that you can configure for an Amazon S3 bucket. It allows you to control access to the objects stored within the bucket by defining rules and permissions.

With this even if you have shared URL of bucket and suppose you have denied the access then that person will not able to access the bucket with url itself.

**Key Elements of Bucket Policy:**

 A bucket policy consists of the following key elements:

Principal: Specifies the user or AWS account that the policy applies to. It can be an IAM user, IAM role, AWS account, or predefined AWS service.

Actions: Defines the specific actions or operations that are allowed or denied on the bucket and its objects, such as "s3:GetObject" or "s3:PutObject".

Resources: Specifies the Amazon Resource Names (ARNs) of the bucket and its objects that the policy applies to.
Effect: Specifies whether the policy allows or denies the specified actions.

Conditions: Optional conditions that further refine the policy based on factors like the requester's IP address or request headers.


**Example Use Cases**: Bucket policies can be used for various purposes, such as:

Granting public access to read-only files in a bucket for static website hosting.

Restricting access to specific IP addresses or VPCs.

Defining access permissions for specific IAM users, groups, or roles.

Enabling cross-account access for sharing resources between AWS accounts.

**Create bucket policy**

1. Create the Bucket

2. Select ACLs Enabled

3. Give Public Access

4. Upload the Object

5. Upload the object and do not give public access to object.

6. Try to access the object. This time you are not able to acces the object.

7. Open our bucket & go to permission tab.

8. Go to bucket policY. You have to enter code to give bucket policy

9. Click on edit bucket policy

10. Copy the Bucket ARN (Amazon Resource Names)

11. Click on Policy generator

12. Select type of policy is S3 Bucket Policy

13. Select effect as Allow

14. Enter principal as * (It means to all the objects)

15. Select actions as All Actions

16. Enter the bucket ARN with forward slash & star<br/>
    Example : arn:aws:s3:::<policy_name>/*

17. Click on add statement and generate policy

18. Now copy the JSON code and paste it in bucket policy section.

19. save changes

20. Now you have given public access to your bucket so you can able to access the object.


## Access Control List (ACL) vs. Bucket Policy

Access Control List (ACL) and Bucket Policy are two mechanisms provided by Amazon S3 to control access to buckets and objects. While they serve similar purposes, there are key differences between them.

## Access Control List (ACL)

Access Control List (ACL) is used to manage access permissions at the object or bucket level. It allows you to grant permissions to specific AWS accounts or predefined groups. ACLs are typically used for individual objects or a small number of objects within a bucket. Here are some key points about ACL:

- Provides object-level or bucket-level access permissions.
- Grants permissions to specific AWS accounts or predefined groups.
- Simple to configure using the AWS Management Console, SDKs, or APIs.
- Fine-grained control over access permissions, allowing read, write, or full control.
- Limited in setting complex rules or policies.
- Suited for managing access permissions to individual objects or a small number of objects within a bucket.

## Bucket Policy

Bucket Policy is an access policy configured at the bucket level. It allows you to define rules and permissions that apply to all objects within the bucket. Here are some key points about Bucket Policy:

- Access policy defined at the bucket level.
- Provides more flexibility in defining access control rules using JSON syntax.
- Allows specifying access permissions based on factors like IP address, request headers, IAM users, or roles.
- Can grant or deny access to a bucket for specific AWS accounts, IAM users, or predefined AWS services.
- Centralized and scalable approach for managing access control across multiple objects.
- Suitable for enforcing consistent access control rules across a large number of objects or complex scenarios.

## Use Cases

Here are some common use cases for ACL and Bucket Policy:

- Use ACL when you need to grant or revoke permissions to specific objects within a bucket. It is useful for managing individual object-level permissions or a small number of objects with unique access requirements.

- Use Bucket Policy when you want to define consistent access control rules for all objects within a bucket. It is beneficial for managing access permissions across a large number of objects or when you require more complex access control scenarios involving multiple users, services, or conditions.

Understanding the differences between ACL and Bucket Policy helps in choosing the appropriate method based on your specific access control requirements.

# LIFE CYCLE MANAGEMENT

 We have seen different storage class of s3. Different storage classes help us to save the cost.<br/>
 earlier have seen how we can change the storage class of our object manually but in real time thousands of objects we have so it will not possible to change storage for each objects manually. Their is an automatic way to change the storage class and that is called Life Cycle Management.

Amazon S3 Life cycle allows to configure a lifecycle for stored objects on S3, to optimize the cost. A Lifecycle configuration is a set of rules that define actions applied to a group of objects.

 In Life Cycle Management based on rules whatever we set our object will automatically move to different storage class.

 ## Example of S3 lifecycle

 Application server, database logs are stored in s3 but logs may not require after a few weeks or months, in this case, you can delete the objects automatically by applying an expiration action.

 Frequency of access requirement of an organization’s documents (financial, media, employee data) Some documents are frequently accessed, but after a few days or months, they are infrequently accessed. After some time, organization may need to archive them as documents are not used anymore but must be retained for regulatory compliance, in this case, you can use transition action.

 ## Creation of Life Cycle rule

 1. Create S3 Bucket

2. Select ACLs Enabled

3. Give Public Access

4. Upload the Object

5. Upload the object and give public access to object.

6. Open our bucket & go to management tab.

7. Click on create life cycle rules.

8. In the life cycle rule wizard, type a name for your rule.

**Note**- Life cycle policy you can apply to all object or to only one object.

9. here choose apply to all object.

10. Select the life cycle rule according to your requiremenet.

11. Choose the storage class and give the number of days you want your object to be there in that particular storage class<br/>
    For ex- Standard IA   and 60 day <br/>
    After creation of object your objet will stay there for 60 days and after 60 days it will move to another storage class.

12. create rule.

With this particular option system will automatically move your object to different storage class.


# Event Notification with SNS Service

SNS stands for Simple Notification Service, and it is a fully managed messaging service provided by Amazon Web Services (AWS). It enables you to send messages or notifications to a variety of endpoint types, such as email, SMS (text messages), mobile push notifications, and even HTTP endpoints.

**Let's see how SNS service you can use**

1. Create S3 Bucket

2. Select ACLs Enabled

3. Give Public Access

4. Create bucket.

5. Go to SNS service.

6. Create SNS topic. Give the name of topic.

7. Select standard .

8. Create topic.

9. Give the policy to SNS topic. For that copy the ARN.

10. Click on edit the ARN and go to access policy and paste the ARN.

11. Save changes.

12. Now add the subscription where you want notification for bucket.

13. Click on SNS subscription 

14. Select email protocol and link the email address on which you want notification.

15. Now you confirm first from you Email id then you will start receiving notifications.

16. Go to your email id and confirm subscription.

17. Now you have to craete an event based on which you will get notification

18. Go to object. Go to event notification.

19. You can select event type like whenever someone create object you want notification or whenever someone delete object you want notification.

20. Select SNS Destination and select SNS topic

21. save changes

22. Now upload our objects and you will get notification onto your email.


# Event Notification with SQS Service

SQS stands for Simple Queue Service, and it is a fully managed message queuing service provided by Amazon Web Services (AWS). SQS enables decoupling of components in distributed systems by allowing one component to send a message to a queue, and another component to retrieve and process that message from the queue.

**Let's see how SQS service can use**

1. Create S3 Bucket

2. Select ACLs Enabled

3. Give Public Access

4. Create bucket.

5. Go to SQS service.

6. Click on craete queue.

7. Select standard and give the name of my queue.

8. In the configuration section you can set:

   **Visisbility Timeout**- When a consumer component retrieves a message from a queue, SQS sets a visibility timeout for that message. During this timeout period, the message is temporarily invisible to other consumers. If the consumer successfully processes the message within the timeout, it deletes the message from the queue. Otherwise, if the consumer fails to process the message within the timeout, the message becomes visible again for other consumers to retrieve and process.

   **Message Retention**: SQS retains messages in the queue until they are processed or explicitly deleted by consumers. This allows for reliable and durable message storage, ensuring that messages are not lost even if consumers are temporarily offline or unavailable.

   Minimum- 1min   Maximum- 14 days

   **Dilevery Delay**- It is the amount of time to delay the first delivery of eaach messages added to queue.

9. Create queue.

10. Click on edit the ARN and go to access policy and paste the ARN.

11. Click on policy generator.

12. Select type as SQS Queue Policy

13. Enter * in principal

14. Select All Actions or Send Messages

15. Enter ARN

16. Click on Add Statement

17. Click on Generate Policy

18. Copy the code & paste the code in the Access policy

19. Click on Save

20. Create S3 Event Notification

21. Go to our bucket

22. Go to Properties tab

23. Go to Event Notification

24. Click on Create Event Notification

25. Enter event name

26. Go to Destination

27. Select SQS Queue

28. Select our SQS Queue

29. Click on Save Changes

30. Upload the object, give public access & open the Object

31. To see the queue messages. Go to SQS

32. Open our SQS

33. Click on Send and receive messages

34. Click on Poll for messages

Now you will able to see messages at queue.

















































