## LAMBDA

Lambda is trigger service . Whenever system is going to perform particular action then code whatever we have given to lambda that needs to be executed. 

Whenever system is executed code only for that time you will be charged and the code whatever you have given that need to be executed within 900 seconds or 15min.


AWS Lambda is a service which computes the code without any server. It is said to be server less compute. The code is executed based on the response of events in AWS services.

To get working with AWS Lambda, we just have to push the code in AWS Lambda service. All other tasks and resources such as infrastructure, operating system, maintenance of server, code monitoring, logs and security is taken care by AWS.

Lambda is also called as Serverless service because to work with this we don't need to create ec2 server.


**LAMBDA - FUNCTIONS SUPPORT CODE**

It support seven programmimng language<br/>
• Node.js<br/>
• Python<br/>
• Ruby<br/>
• Java<br/>
• Go<br/>
• C#<br/>
• Powershell<br/>


**LAMBDA - ADVANTAGES**

**Ease of Working with Code**: AWS Lambda gives you the infrastructure to upload your code. It takes care of maintaining the code and triggers the code whenever the required event happens. It allows you to choose the memory and the timeout required for the code. AWS Lambda can also execute parallel requests as per the event triggers.

**Logs Provision**: AWS Lambda gives the details of number of times a code was executed and time taken for execution, the memory consumed etc. AWS CloudWatch collects all the logs, which helps in understanding the execution flow and in the debugging of the code.

**Billing based on Usage**: AWS Lambda billing is done on memory usage, request made and the execution, which is billed in increments of minimum 100ms. So for a 500ms execution, the billing will be after every 100ms. If you specify your AWS lambda code to be executed in 500ms and the time taken to execute is just 200ms, AWS will bill you only for the time taken that is 200ms of execution instead of 500ms. AWS always charges for the execution time used. You need not pay if the function is not executed.

**Multi Language Support**: AWS Lambda supports popular languages such as Node. js, Python, Java, C# and Go. These are widely used languages and any developer will find it easy to write code for AWS Lambda.


**Let's create lambda**

In this whenevr we upload object in s3 bucket then system is executing trigger with the help of lambda and the details whatever we have written in object is going to store under our table called DynamoDb.

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


## MONITORING SERVICE - CLOUDWATCH

Amazon Web Services (AWS) monitoring is a set of practices we can use to verify the security and performance of our AWS resources and data. These practices rely on various tools and services to collect, analyze, and present data insights.

With this monitoring service we can monitor our EC2 machine.


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

1. To enable detailed monitoring click on manage detailed monitoring.

2. Check enable & click on save

Now system is start displaying us details about the particular EC2 machine.

3. We are getting all these matric from Cloud watch service.

4. Go to Cloud Watch

5. Click on Metrics

6. Click on All Metrics

7. Click on EC2

8. Click on per instance metrics

9. Search for our instance with the help of instance id. We can get it from EC2 instance.

10. We can select the metric name & See more details about the graph.


## BILLING ALARM

We can monitor your estimated AWS charges by using Amazon CloudWatch. When we enable the monitoring of estimated charges for our AWS account, the estimated charges are calculated and sent several times daily to CloudWatch as metric data. Billing metric data is stored in the US East (N. Virginia) Region and represents worldwide charges.

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


## CALCULATOR

AWS Pricing Calculator is a web-based planning tool that you can use to create estimates for your AWS use cases. AWS Pricing Calculator is provided at no charge.

1. Go to aws pricing calculator service.

2. We can search by location type or search all services. Choose search by location type

3. select mumbai region

4. Find ec2 services.

5. Configure EC2 instances. 

6. save and view summary


## CLOUD TRAIL

AWS Cloud Trail is an AWS service that helps us enable governance, compliance, and operational and risk auditing of our AWS account. Actions taken by a user, role, or an AWS service are recorded as events in Cloud Trail. All the activities can be tracked by user using cloud trail. By default only root user can see the event history. If IAM user want to see the event history we need to attach the role (Cloud Trail) to the IAM User

It is going to track eaca and every activity in aws.

1. Go to Cloud Trail

2. Click on Event History

3. Download Events




