# LAMBDA

Lambda is a trigger-based service that executes a specific code whenever a particular action is performed in the system.<br>

Lambda: Refers to "AWS Lambda," which is a serverless computing service provided by Amazon Web Services (AWS). It allows you to run code without provisioning or managing servers. You upload your code to Lambda, and it automatically handles the infrastructure and scaling for you.<br>

Trigger-based service: AWS Lambda is a trigger-based service, meaning it responds to events or triggers that occur within the AWS ecosystem or integrated services. These triggers can be events like changes to data in a database, updates to files in an S3 bucket, HTTP requests to an API Gateway, and more.<br>

Executes a specific code: When Lambda is triggered, it executes a specific piece of code that you have written and uploaded to Lambda. This code can be written in various programming languages supported by Lambda, such as Python, Node.js, Java, etc.<br>

Particular action: The code in Lambda is executed in response to a specific event or action. For example, if you have a Lambda function that processes images, it could be triggered whenever a new image is uploaded to an S3 bucket.<br>

System: In this context, the "system" refers to the AWS environment or other integrated services where the events or triggers occur.<br>

Whenever system is executed code only for that time you will be charged and the code whatever you have given that need to be executed within 900 seconds or 15min.<br>

AWS Lambda is a service which computes the code without any server. It is said to be server less compute. The code is executed based on the response of events in AWS services.<br>

To get working with AWS Lambda, we just have to push the code in AWS Lambda service. All other tasks and resources such as infrastructure, operating system, maintenance of server, code monitoring, logs and security is taken care by AWS.<br>

In summary, AWS Lambda is a service that runs your code in response to events or triggers that occur in the AWS environment or integrated services. It allows you to create custom logic without managing the underlying infrastructure, providing a serverless and scalable solution for event-driven applications and workflows.<br>

**AWS Lambda - Supported Programming Languages**

It support seven programmimng language<br/>
• Node.js<br/>
• Python<br/>
• Ruby<br/>
• Java<br/>
• Go<br/>
• C#<br/>
• Powershell<br/>


**Advantages Of AWS Lambda**

**Ease of Working with Code**: AWS Lambda gives you the infrastructure to upload your code. It takes care of maintaining the code and triggers the code whenever the required event happens. It allows you to choose the memory and the timeout required for the code. AWS Lambda can also execute parallel requests as per the event triggers.

**Logs Provision**: AWS Lambda gives the details of number of times a code was executed and time taken for execution, the memory consumed etc. AWS CloudWatch collects all the logs, which helps in understanding the execution flow and in the debugging of the code.

**Billing based on Usage**: AWS Lambda billing is done on memory usage, request made and the execution, which is billed in increments of minimum 100ms. So for a 500ms execution, the billing will be after every 100ms. If you specify your AWS lambda code to be executed in 500ms and the time taken to execute is just 200ms, AWS will bill you only for the time taken that is 200ms of execution instead of 500ms. AWS always charges for the execution time used. You need not pay if the function is not executed.

**Multi Language Support**: AWS Lambda supports popular languages such as Node. js, Python, Java, C# and Go. These are widely used languages and any developer will find it easy to write code for AWS Lambda.


**Let's create lambda**

We will create a Lambda function that triggers whenever an object is uploaded to an S3 bucket. The Lambda function will extract the information from the uploaded object and store it in our DynamoDB table. Follow the steps below to set up the Lambda function.

1. To work with lambda prequisites is to create IAM role.

2. Create IAM Role

3. Go to IAM Service

4. Click on Roles

5. Click on Create Role

6. Select AWS Services

7. Select Lambda & Click on Next: Permissions

8. Search AmazonDynamoDBFullAccess

9. Enter the Role Name

10. Click on Create Role.

11. Now Create s3 bucket.

12. Give the name of s3 bucket.

13. Enable ACL and Give public access.

14. Now create DynamoDb table

15. Enter the table Name (newtable)

16. Enter partition key (unique)

17. Click on Create table.

18. Now go to lambda service

19. Click on Create Function. Select author from scratch.

20. Enter the Function Name

21. Select Runtime (Python 3.7)

22. Click on Change default execution role

23. Select the use an existing role

24. Select the role we have created

25. Click on Create function.

26. Give the lambda python code<br/>
    import boto3<br/>
    from uuid import uuid4<br/>
    def lambda_handler(event, context):<br/>
    s3 = boto3.client("s3")<br/>
    dynamodb = boto3.resource('dynamodb')<br/>
    for record in event['Records']:<br/>
        bucket_name = record['s3']['bucket']['name']<br/>
        object_key = record['s3']['object']['key']<br/>
        size = record['s3']['object'].get('size', -1)<br/>
        event_name = record ['eventName']<br/>
        event_time = record['eventTime']<br/>
        dynamoTable = dynamodb.Table('newtable')<br/>
        dynamoTable.put_item(<br/>
            Item={'unique': str(uuid4()), 'Bucket': bucket_name, 'Object': object_key,'Size': size, 'Event': event_name, 'EventTime': event_time})

27. Click on Deploy

28. Click on Add Trigger

29. Select trigger as S3

30. Select the bucket

31. Select event type as per requirement (All Object Create Events) means on which event based we want to execute this trigger.

32. Check the acknowledge

33. Click on Add

34. Upload the Object in S3 Bucket & Give Public Access to Object.

35. Now check the DynamoDB table

36. Click on Run

When we upload object in s3, lambda trigger will execute and we will find table in DynamoDb.


# Monitoring Service - CloudWatch

In Amazon Web Services (AWS), monitoring is like having a watchful guardian that keeps an eye on your AWS resources and data. It ensures their security and performance so you can have peace of mind while running your applications and services in the cloud. One of the important tools for monitoring in AWS is called "Amazon CloudWatch."

#### What Does CloudWatch Do?
Amazon CloudWatch collects and tracks data from various AWS resources in real-time. It keeps a close watch on your virtual machines (EC2 instances), databases, storage, and other services you use in AWS. CloudWatch takes important measurements and stores them securely for analysis.

#### Key Benefits of CloudWatch:

1. **Performance Insights:** Keep track of how your AWS resources are performing, identifying any areas that need improvement.

2. **Alerts and Alarms:** Set up custom alerts and alarms based on specific thresholds. Get notified if any metric crosses the threshold, enabling quick responses to issues.

3. **Dashboards and Visualizations:** CloudWatch creates customizable dashboards and visualizations, providing an easy-to-understand overview of your resource health.

4. **Historical Analysis:** Store historical data to analyze trends and patterns over time.

5. **Integration with Other Services:** CloudWatch seamlessly integrates with other AWS services, making it a crucial component of your monitoring and operational setup.

#### Monitoring EC2 Instances:

One of the most common use cases for CloudWatch is monitoring EC2 instances, which are virtual machines in the AWS cloud. With CloudWatch, you can keep track of key metrics like CPU utilization, network traffic, disk performance, and more for each running EC2 instance.

#### Setting Up Monitoring:

To start monitoring your AWS resources with CloudWatch, follow these simple steps:

1. **Enable CloudWatch:** Enable CloudWatch for the AWS services and resources you want to monitor.

2. **Data Collection:** CloudWatch automatically collects data from your resources, so no manual configuration is needed.

3. **View Insights:** Once data is collected, you can easily view and analyze it through CloudWatch's intuitive interface.

## Usage:

CloudWatch is essential for ensuring the smooth and secure operation of your AWS resources. It empowers you to make informed decisions, proactively respond to potential issues, and optimize the performance of your applications and services.

In summary, CloudWatch is a valuable monitoring service in AWS that helps you keep your resources in check, detect issues early, and ensure your applications and services run smoothly in the cloud.



**MONITORING SERVICE - TYPES**

• Basic Monitoring<br/>
• Detailed Monitoring

**Basic Monitoring**: It is by default enabled.These metrics will be updated in every 5 minutes. It is free service.

**Detailed Monitoring**: Data is available in one minute. We are charged per metric that is sent to CloudWatch.


**To check basic Monitoring**

1. Create an EC2 Machine

2. Go to Monitoring Tab

3. We are not able to see graph because it will take 5 minutes to update.


**To check detailed Monitoring**

1. To enable detailed monitoring, click on manage detailed monitoring in ec2.

2. Check enable & click on save<br>

Now system is start displaying us details about the particular EC2 machine.

3. We are getting all these matric from Cloud watch service.

4. Go to Cloud Watch

5. Click on Metrics

6. Click on All Metrics

7. Click on EC2

8. Click on per instance metrics

9. Search for our instance with the help of instance id. We can get it from EC2 instance.

10. We can select the metric name & See more details about the graph.


# Billing Alarm - Keep Track of Your AWS Costs

We can monitor our estimated AWS charges by using Amazon CloudWatch. When we enable the monitoring of estimated charges for our AWS account, the estimated charges are calculated and sent several times daily to CloudWatch as metric data.<br>
The Billing Alarm acts as your financial watchdog for your AWS account. It helps you monitor and track the estimated spending on AWS services, much like a diligent assistant keeping an eye on your expenses.

#### How Does it Work?

When you enable the Billing Alarm, AWS will calculate your estimated charges multiple times a day and send this information to Amazon CloudWatch. CloudWatch acts as a secure vault, storing all the cost-related data.

#### Why Use Billing Alarm?

The Billing Alarm acts as a spending limit for your AWS account. You can set a specific budget that you don't want to exceed. If your estimated charges approach or surpass that limit, CloudWatch will raise an alarm. It serves as a warning signal, alerting you when your spending reaches a predefined threshold.

#### Example:

Imagine you're running a website on AWS, and you want to ensure you don't spend more than $50 per month. By setting up a Billing Alarm with CloudWatch to monitor your spending, you'll receive an immediate notification if your estimated charges reach or exceed $50. This way, you can take control of your costs and avoid overspending.

#### Note:

The billing metric data is securely stored in a special location (US East - N. Virginia Region), covering your AWS charges from around the world.

Using Billing Alarms and CloudWatch empowers you to be financially savvy with your AWS spending and prevents any surprises when it comes to your bills!

By keeping track of your AWS costs with Billing Alarms, you can ensure you stay within your budget and enjoy a seamless experience using AWS services. Happy cloud computing!

**To anable the billing you can these steps**
1. Go to My Account

2. Click on my Account

3. Click on Billing Preferences

4. Check Receive billing alerts

5. Click on save preferences

6. Change region to N. Virginia

7. Go to Cloud Watch

8. Click on Alarm

9. Click on in Alarm

10. Click on Create alarm

11. Click on Select metric

12. Click on billing

13. We have a option to select billing on service wise or total estimated charge.

14. Click on total estimated charge

15. Select currency

16. Click on select metric

17. Select threshold type as static

18.  We have a option to Select greater, greater/equal, lower, lower/equal. Select greater

19. Enter the amount.

20. Click on next

21. Select create new topic

22. Enter email address & Click on Create topic

23. Click on Next

24. Enter alarm name

25. Click on Next

26. Click on Create alarm

27. Check our email & Confirm Email


# CALCULATOR

AWS Pricing Calculator is a web-based planning tool that you can use to create estimates for your AWS use cases. AWS Pricing Calculator is provided at no charge.

1. Go to aws pricing calculator service.

2. We can search by location type or search all services. Choose search by location type

3. select mumbai region

4. Find ec2 services.

5. Configure EC2 instances. 

6. save and view summary


# Cloud Trail: Track your AWS Activities

#### What is CloudTrail?

AWS CloudTrail is like a security camera for your AWS account. It helps you keep an eye on all the actions performed by users, roles, or AWS services. Think of it as a detailed activity log that records everything happening in your AWS world.

#### How Does it Work?

Whenever someone does something in your AWS account, CloudTrail records it as an event. These events are like footprints that show who did what and when they did it. It's like having a trail of breadcrumbs to follow.

#### Why Use CloudTrail?

CloudTrail helps you ensure governance, compliance, and risk auditing. It's like having a watchful eye to maintain control and security in your AWS environment. You can see what changes were made, who made them, and stay on top of your account's security.

#### Example:

Let's say you have a team of developers working on your AWS projects. With CloudTrail, you can see who deployed a new server, who changed the security settings, and who accessed sensitive data. It's like having a security camera that captures all the important actions.

#### Note:

By default, only the root user can see the event history. But if you want your IAM users to see the event history, you can attach the CloudTrail role to their IAM accounts. It's like giving them permission to watch the security camera too.

With CloudTrail, you have better control, security, and understanding of what's happening in your AWS world. It's like having a superpower to keep track of your AWS activities!

It is going to track each and every activity in aws.

1. Go to Cloud Trail

2. Click on Event History

3. Download Events




