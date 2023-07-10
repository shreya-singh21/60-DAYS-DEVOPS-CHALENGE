# AWS EC2 Auto Scaling: Creating an Auto Scaling Group with Load Balancer

Auto Scaling in AWS EC2 allows you to automatically adjust the number of EC2 instances in a group based on the demand to ensure optimal performance and cost efficiency. In this tutorial, I will walk you through the steps to create an Auto Scaling group with a load balancer.

## Step 1: Create Launch Configuration / Launch Template

The first step is to create a Launch Configuration or Launch Template. This configuration/template specifies the instance type, AMI, security groups, key pair, and other settings for the instances in your Auto Scaling group. It acts as a blueprint for launching new instances.

## Step 2: Create Topic in SNS (Simple Notification Service)

Next, create a topic in the AWS Simple Notification Service (SNS). The SNS topic allows you to send notifications about events related to your Auto Scaling group. You can configure email notifications, SMS alerts, or trigger actions in other AWS services based on these notifications.

## Step 3: Create Auto Scaling Group

Now, it's time to create the Auto Scaling group. The Auto Scaling group is responsible for managing the EC2 instances based on the defined policies and configurations. Specify the minimum and maximum number of instances you want in the group, along with the desired capacity.

## Step 4: Create Application Load Balancer

To distribute the incoming traffic across the instances in your Auto Scaling group, you need to create an Application Load Balancer (ALB). The ALB acts as a single point of contact for clients and intelligently routes requests to healthy instances.

## Step 5: Create Target Group

A Target Group is associated with the ALB and defines the targets (instances) that the ALB should distribute traffic to. Create a Target Group and configure the health checks and routing rules for the instances in your Auto Scaling group.

## Step 6: Create Alarm in CloudWatch

CloudWatch provides monitoring and alerting capabilities for AWS resources. Create an alarm in CloudWatch to monitor metrics such as CPU utilization, network traffic, or request count. Set threshold values to trigger the alarm when the specified conditions are met.

## Step 7: Add Policy in Auto Scaling

In this step, add a scaling policy to your Auto Scaling group. The policy defines how the group should scale based on the alarm triggers. You can configure scaling actions such as adding or removing instances and set the cooldown period to prevent rapid scaling.

By following these steps, you can create an Auto Scaling group with a load balancer in AWS EC2. This setup ensures that your application scales seamlessly based on the demand, maintains high availability, and optimizes cost efficiency.


## :movie_camera: Helpful Video Tutorials
This is one way to create an Auto Scaling group with a load balancer in AWS EC2. Keep in mind that there are various approaches to achieve auto scaling based on different requirements. For more reference and detailed information, you can consult the AWS documentation or explore online tutorials. Here are a few helpful tutorial links:

- [AWS User Group India - AWS Auto Scaling Tutorial](https://www.youtube.com/watch?v=vrL-WpXNook&ab_channel=AWSUserGroupIndia)
- [Gaurav Sharma - AWS Auto Scaling Deep Dive](https://www.youtube.com/watch?v=E2I4GT-AqHY&ab_channel=GauravSharma)
 

 # AWS Status Check

AWS Status Check is a monitoring feature provided by Amazon Web Services (AWS) that ensures the health and availability of your EC2 instances. It performs automated checks on various components of an instance, including the underlying hardware, operating system, and software configuration.

## Key Points

- **Purpose**: AWS Status Check verifies the overall system status of an EC2 instance and alerts you if any issues are detected. It ensures that your instances are running properly and can handle incoming traffic.
- **Two Types of Status Checks**: AWS performs two types of status checks:
  - **System Status Checks**: These checks monitor the AWS hardware and systems that EC2 instances run on. A failing system status check will typically require intervention from AWS to be fixed. Examples of problems that can cause system status checks to fail include loss of network connectivity, loss of system power, software issues on the physical host, and hardware issues on the physical host that impact network reachability.
  - **Instance Status Checks**: These checks indicate a problem with instance configuration or software. Examples of problems that can cause instance status checks to fail include failed system status checks, incorrect networking or startup configuration, exhausted memory, and corrupted file system.

- **EC2 Status Check**: The EC2 Status Check provides information about the status of the system and instance checks. The status is represented as a fraction, such as 2/2, 1/2, or 0/2. It indicates the number of checks that have passed out of the total number of checks.
  - 2/2: Both the system check and instance check have passed.
  - 1/2: The system check has passed, but the instance check has failed.
  - 0/2: Both the system check and instance check have failed.

## Monitoring Interval

AWS Status Check runs every minute by default. It continuously monitors the instance's status and reports any failures or warnings that require attention.

## Results and Access

You can access the status check results through the AWS Management Console, Command Line Interface (CLI), or APIs. These tools provide visibility into the status of your instances and allow you to identify potential problems.

## Automatic Recovery

In case of a failure or issue detected during a status check, AWS automatically attempts to recover the instance. It may reboot the instance or take other corrective actions to restore its functionality.

AWS provides an auto recovery feature that enables automatic recovery of instances when a system status check failure occurs. If an instance becomes unreachable due to an underlying hardware failure or a problem that requires AWS involvement to repair, the instance is automatically recovered.

#### To enable auto recovery for an instance, follow these steps:

1. Go to the EC2 service in the AWS Management Console.
2. Navigate to the "Instances" section.
3. Select the desired instance.
4. In the "Instance Settings" tab, click on "Change" next to "Auto Recovery behavior".
5. Make sure the auto recovery behavior is enabled.
6. Save the changes.

With auto recovery enabled, AWS will automatically attempt to recover the instance in case of a system status check failure.

## Monitoring and Maintenance

Regularly monitoring the status checks of your EC2 instances is crucial to maintaining their reliability and availability. By promptly addressing any reported issues, you can ensure the performance and stability of your instances in your AWS environment.

## Protect Instance from Termination

We can enable termination protection for our EC2 instances to prevent accidental termination. When termination protection is enabled, it adds an extra layer of safety and ensures that instances cannot be terminated without explicitly disabling the protection.

To protect an instance from termination, follow these steps:

1. Create a Linux EC2 Machine.
2. Select the EC2 instance that you want to protect.
3. Enable the checkbox for termination protection.
4. Click on "Save" to apply the changes.

With termination protection enabled, you can help prevent accidental terminations of your important instances.

To disable termination protection and allow the instance to be terminated, follow these steps:

1. Select the EC2 instance that has termination protection enabled.
2. Go to "Actions".
3. Navigate to "Instance Settings" and click on "Change Termination Protection".
4. Disable the termination protection by unchecking the checkbox.
5. Save the changes.

By following these steps, you can protect your EC2 instances from accidental termination and ensure the safety of your critical workloads.

Please note that enabling termination protection is a best practice to prevent unintended termination, but it should be used judiciously, considering the specific needs and requirements of your environment.


## Protect Instance from Stop

You can enable stop protection for your EC2 instances to prevent accidental stopping of instances. When stop protection is enabled, it adds an extra layer of safety and ensures that instances cannot be stopped without explicitly disabling the protection.

To protect an instance from being stopped, follow these steps:

1. Create a Linux EC2 Machine.
2. Select the EC2 instance that you want to protect.
3. Go to "Actions" and navigate to "Instance Settings".
4. Click on "Change Stop Protection".
5. Enable the checkbox for stop protection.
6. Click on "Save" to apply the changes.

With stop protection enabled, you can help prevent accidental stops of your important instances.

To disable stop protection and allow the instance to be stopped, follow these steps:

1. Select the EC2 instance that has stop protection enabled.
2. Go to "Actions" and navigate to "Instance Settings".
3. Click on "Change Stop Protection".
4. Disable the stop protection by unchecking the checkbox.
5. Save the changes.

By following these steps, you can protect your EC2 instances from accidental stopping and ensure the availability of your critical workloads.

Please note that enabling stop protection is a best practice to prevent unintended stops, but it should be used judiciously, considering the specific needs and requirements of your environment.


## Shutdown Behavior

The shutdown behavior of an EC2 instance determines its response when a shutdown command is initiated. By default, when you initiate a shutdown from an Amazon EBS-backed instance using a command like `shutdown` or `power off`, the instance stops. However, using the `halt` command will not issue a power-off command and the instance will remain running in a halted state.

To change the shutdown behavior to terminate the instance instead of stopping it, follow these steps:

1. Select the EC2 instance for which you want to change the shutdown behavior.
2. Go to "Actions" and navigate to "Instance Settings".
3. Click on "Change Shutdown Behavior".
4. Select the option to "Terminate" the instance on shutdown.
5. Click on "Save" to apply the changes.

With the shutdown behavior set to terminate, when you issue a shutdown command, the instance will be terminated instead of stopping. This ensures that the instance is fully terminated and no longer incurs any charges.

To test the shutdown behavior, connect to the EC2 machine, switch to the root user, and initiate a shutdown using the `shutdown` command. After a few minutes, the system will automatically terminate the machine.

Please note that changing the shutdown behavior to terminate should be done carefully, considering the impact on any running processes or data on the instance. Ensure that you have proper backups and take necessary precautions before making this change.


## Scale Up

Scale Up, also known as vertical scaling, is a method of increasing your computing capacity by adding additional resources to your EC2 instance. This typically involves upgrading the central processing unit (CPU), random access memory (RAM), or hard disk drive (HDD) to enhance the performance of your instance.

To scale up your EC2 instance, follow these steps:

1. Select the EC2 instance for which you want to scale up.
2. Go to "Actions" and navigate to "Instance Settings".
3. Click on "Change Instance Type".
4. Choose a new instance type that offers higher CPU, RAM, or other desired resources.
5. Note that changing the instance type requires stopping the instance temporarily.
6. Click on "Apply" to change the instance type.

Additionally, if you want to increase the size of your HDD, follow these steps:

1. Go to "Elastic Block Store" and select the volume associated with your EC2 instance.
2. Go to "Actions" and choose "Modify Volume".
3. Increase the size of the volume as per your requirements.
4. Click on "Modify" and confirm the action by clicking "Yes".

Please note that expanding the root and user volumes can only be done once every 6 hours, and it's not possible to reduce the HDD size after increasing it.

## Scale Down

Scale Down is the opposite of Scale Up and involves reducing the CPU, RAM, or other resources of your EC2 instance.

To scale down the CPU and RAM of your EC2 instance, follow the same steps mentioned for Scale Up and choose an instance type that offers lower resources.

Please keep in mind that scaling down the resources of an EC2 instance may impact its performance and the applications running on it. Ensure that you consider the requirements of your workload and properly test the changes before applying them to production environments.

## Scale Out and Scale In

Scale Out and Scale In, also known as horizontal scaling, involves adjusting the number of instances in your application's fleet to meet the changing demands of your workload. This is typically achieved using the Auto Scaling feature provided by AWS.

Scale Out refers to increasing the number of instances in your application's fleet to handle higher traffic or workload. This can be done automatically by configuring Auto Scaling policies based on metrics such as CPU utilization or network traffic.

Scale In refers to decreasing the number of instances in your application's fleet to optimize resource utilization and cost. Auto Scaling can automatically terminate excess instances when the demand decreases.

To implement Scale Out and Scale In using Auto Scaling, follow these steps:

1. Set up an Auto Scaling group that specifies the desired minimum and maximum number of instances.
2. Configure scaling policies that define the conditions for scaling out and scaling in, such as CPU utilization thresholds or network traffic patterns.
3. Auto Scaling continuously monitors the specified metrics and automatically adds or removes instances as needed based on the scaling policies.
4. This allows your application to dynamically scale in response to changing demand, ensuring optimal performance and cost efficiency.

Auto Scaling also provides additional features such as scheduled scaling, which allows you to define scaling actions based on a specific schedule, and predictive scaling, which uses machine learning algorithms to anticipate demand and proactively scale your instances.

By implementing Scale Out and Scale In using Auto Scaling, you can ensure that your application can handle varying workloads efficiently while optimizing resource utilization and cost.

Note: It's important to carefully plan and test your Auto Scaling configurations to ensure they align with your application's requirements and performance expectations.
