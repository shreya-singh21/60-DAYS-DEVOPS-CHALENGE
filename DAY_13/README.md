## LAMBDA

Lambda is trigger service . Whenever system is going to perform particular action then code what ever we have given to lambda that needs to be executed. 

AWS Lambda is a service which computes the code without any server. It is said to be server less compute. The code is executed based on the response of events in AWS services.

To get working with AWS Lambda, we just have to push the code in AWS Lambda service. All other tasks and resources such as infrastructure, operating system, maintenance of server, code monitoring, logs and security is taken care by AWS.


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

1. To use lambda first we need to create IAM role.

2. Create IAM Role

3. Go to IAM Service

4. Click on Roles

5. Click on Create Role

6. Select AWS Services

7. Select Lambda & Click on Next: Permissions

8. Search AmazonDynamoDBFullAccess

9. Enter the Role Name

10. Click on Create Role

11. Now Create s3 bucket.

12. Give the name of s3 bucket.

13. Give public access

14. Now create DynamoDb table

15. Enter the table Name 

16. Enter partition key

17. Click on Create table

18. Now go to lambda service

19. Click on Create Function

20. Enter the Function Name

21. Select Runtime (Python 3.6)

22. Click on Change default execution role

23. Select the use an existing role

24. Select the role we have created

25. Click on Create function

26. Give the lambda python code

27. Click on Deploy

28. Click on Add Trigger

29. Select trigger as S3

30. Select the bucket

31. Select event type as per requirement (All Object Create Events)

32. Check the acknowledge

33. Click on Add

34. Upload the Object in S3 Bucket & Give Public Access to Object

35. Now check the DynamoDB table

36. Click on Run
