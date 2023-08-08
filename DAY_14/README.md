# CLOUD FORMATION

AWS CloudFormation is a service provided by Amazon Web Services (AWS) that allows you to create and manage AWS resources using templates. It enables you to define your infrastructure as code, allowing for automated provisioning, deployment, and management of your AWS resources in a consistent and repeatable manner.

**Key features of AWS CloudFormation**:

**Infrastructure as Code (IaC)**: CloudFormation templates are written in JSON or YAML and define the desired state of your AWS resources. By using code to define your infrastructure, you can version control, test, and manage it just like any other software application.

**Template-based provisioning**: CloudFormation uses templates to describe the resources and their configurations in a declarative manner. You specify what resources you want, their properties, and any dependencies between them. AWS CloudFormation takes care of creating, updating, and deleting these resources based on the template.

**Stack management**: In CloudFormation, a stack is a collection of AWS resources that are created and managed as a single unit. You create, update, and delete stacks to manage the entire lifecycle of your application and its associated resources.

**Resource consistency**: With CloudFormation, you can ensure that your AWS resources are created and configured consistently across different environments, making it easier to maintain and troubleshoot your infrastructure.

**Rollback and error handling**: If an error occurs during the creation or update of a stack, CloudFormation can automatically roll back the changes to a previous known state, helping to avoid incomplete or misconfigured resources.

**Stack updates**: As your application evolves, you can use CloudFormation to update your stacks with new resources or changes to existing resources. CloudFormation will intelligently apply only the necessary changes to bring your stack to the desired state.

**Example use case**:

Let's say you want to deploy a web application that consists of an Amazon EC2 instance, an Amazon RDS database, and an Elastic Load Balancer (ELB). Instead of manually creating these resources and configuring them, you can use CloudFormation to define a template that describes all the necessary resources, their properties, and relationships. You can include parameters to customize the deployment, such as instance type, database credentials, and more.

Once the template is ready, you can use CloudFormation to create a stack based on that template. CloudFormation will automatically provision the EC2 instance, RDS database, and ELB, and set up the necessary connections and configurations between them. If you need to update the stack later, you can modify the template and apply the changes through CloudFormation.

Using AWS CloudFormation, you can easily manage complex infrastructure setups and application deployments, saving time and ensuring consistency across your AWS resources.


**We can create the AWS Infrastructure in three ways**

• Graphical User Interface<br/>
• Command Line Interface<br/>
• Cloud Formation<br/>


**Let's start creation of Cloud Formation**

1. Go to Cloud Formation

2. Click on Create stack

3. There we will find 3 options of preparing template<br/>
    • Template is ready - In this we can select our existing template.<br/>
    • Use a sample template - In this we have given saveral option like LAMP Stack. We can select them and use them.<br/>
    • Create template in designer - In this we can create our own template.<br/>

4. For our case select use a sample template.

5. Select the sample code (Lamp Stack)<br/>
   LAMP - Linux Apache MySQL PHP

6. Click on Next

7. Enter stack name, Database password, database root password & database user

8. Select Instance type (t2.micro)

9. Select key name

10. Click on Next

11. Enter tags

12. Click on Next

13. Click on Create stack

14. Now go to EC2

15. Check instance.

16. We will find the instance has been created.

17. If we delete the Stack then we will see the EC2 Machine is automatically deleted.


## ELASTIC BEANSTALK

AWS Elastic Beanstalk helps to quickly deploy and manage applications in the AWS Cloud without having to worry about the infrastructure that runs those applications. It is mainly use by the developers.

Developers write the code, they upload the code into Elastic Beanstalk. Infrastructure will be created automatically for testing the application.It abstracts the underlying infrastructure complexities, allowing developers to focus on writing code rather than managing servers.

Elastic Beanstalk provides developers and systems administrator an easy, fast way to deploy and manage the applications without having to worry about AWS infrastructure.


**Let's create the Elastic Beanstalk**

1. Go to Elastic Beanstalk

2. Click on create application

3. Enter application name

4. Select the platform - python

5. Now there are two option by whic we can upload our code.
   • Sample Application code
   • Upload your code

6. Select Application Code as Sample Application

7. Click on create application

8. Check EC2 instance, cloudwatch and s3.

9. We will get the url and from there we can access the default application.


## TRUSTED ADVISIOR

AWS Trusted Advisor is an online tool provided by Amazon Web Services (AWS) that helps customers optimize their AWS environment and improve operational performance, security, and cost efficiency. It provides real-time guidance and best practices based on AWS's extensive experience in managing cloud infrastructures.

**Trusted Advisor checks the following five categories**<br/>

• Cost Optimization<br/>
• Security<br/>
• Fault Tolerance<br/>
• Performance<br/>
• Service Limits<br/>


**Key features of AWS Trusted Advisor**:

**Cost Optimization**: Trusted Advisor analyzes AWS usage and recommends ways to optimize costs. It identifies potential cost savings opportunities, such as terminating idle or underutilized instances, resizing instances for better cost efficiency, and recommending reserved instance purchases.

**Performance**: Trusted Advisor evaluates the performance of resources and suggests improvements to enhance application performance. It looks for potential bottlenecks and identifies opportunities to improve performance by adjusting configurations or adding resources.

**Security**: Trusted Advisor assesses the security of AWS resources and provides recommendations to enhance security and compliance. It checks for open security groups, unused IAM (Identity and Access Management) credentials, and other potential security vulnerabilities.

**Fault Tolerance**: Trusted Advisor examines the fault tolerance of resources and suggests improvements to enhance high availability and resilience. It looks for single points of failure and provides recommendations to distribute resources across multiple Availability Zones for better fault tolerance.

**Service Limits**: Trusted Advisor checks the service limits for various AWS resources and alerts users when they are nearing their limits. This helps users avoid hitting resource limits and ensures smooth operation of their applications.


## SIMPLE EMAIL SERVICE

Amazon Simple Email Service (SES) is a cloud-based email sending service provided by Amazon Web Services (AWS). It allows developers and businesses to send transactional, marketing, and notification emails to their customers and users in a reliable and scalable manner. SES simplifies the process of sending emails and ensures high deliverability rates.


**Key features of Amazon SES**:

**Email Sending**: SES allows you to send both individual and bulk emails using a simple API or SMTP (Simple Mail Transfer Protocol) interface. You can integrate SES with your applications, websites, or other systems to send emails to your recipients.

**High Deliverability**: SES employs various mechanisms to improve email deliverability and avoid emails being marked as spam. It uses content filtering, sender reputation monitoring, and bounce handling to ensure that emails reach the recipient's inbox.

**Email Tracking**: SES provides tracking features that allow you to monitor the delivery status of your emails. You can track metrics such as bounces, complaints, and delivery attempts, which helps in understanding the email delivery performance.

**Easy Integration**: SES integrates seamlessly with other AWS services like AWS Lambda, AWS S3, AWS SNS, and AWS IAM, enabling you to build powerful and flexible email workflows.

**Bounce and Complaint Handling**: SES automatically handles bounce-backs (undeliverable emails) and complaints (emails marked as spam) and manages the suppression list, ensuring that you don't send emails to invalid addresses or recipients who have opted out.

Let's create the SES service**

1. Go to SES Service

2. Click on Create Identity

3. In this we have two options<br/>
    • we can link our domain<br/>
    • we can give email address

4. Select email address

5. Enter our email address

6. Click on Create identity

7. Go to our email

8. Validate it by giving confirmation

9. Now go again to SES.

10. Click on Send Test Email

11. Select scenario as custom

12. Enter custom recipient's email

13. Enter Subject

14. Enter body

15. Click on Additional Configurations

16. Click on Send test email


**Note** - We can link this SES service with our website also. If we are using any html website then we can link SES with the help of SMTP (Simple Mail Transfer Settings). If we are using any wordpress websites then In Wordpress we have some plugins to send emails using SMTP.











