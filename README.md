# DevOps 60-Day Challenge

Welcome to the DevOps 60-Day Challenge! This challenge is designed to help you learn and explore various aspects of DevOps, including cloud computing, infrastructure automation, continuous integration and deployment, and more. Each day, you will focus on a specific topic and document your learnings in a corresponding folder.

## Roadmap

Here is an overview of the 60-day roadmap:

1. [Day 1: Cloud Computing](https://github.com/shreya-singh21/60-DAYS-DEVOPS-CHALENGE/tree/master/DAY_1)
2. [Day 2: Linux Commands and File and Folder Transfer between Local Machine and EC2 using SCP](https://github.com/shreya-singh21/60-DAYS-DEVOPS-CHALENGE/tree/master/DAY_2)
3. [Day 3: AWS Elastic IP](https://github.com/shreya-singh21/60-DAYS-DEVOPS-CHALENGE/tree/master/DAY_3)
4. [Day 4: Placement Groups,Elastic Load Balancer](https://github.com/shreya-singh21/60-DAYS-DEVOPS-CHALENGE/tree/master/DAY_4)
5. [Day 5: AWS EC2 Auto Scaling, AWS Status Check, Automatic Recovery](https://github.com/shreya-singh21/60-DAYS-DEVOPS-CHALENGE/tree/master/DAY_5)
## Day 1: Cloud Computing

In the [Day 1 folder](https://github.com/shreya-singh21/60-DAYS-DEVOPS-CHALENGE/tree/master/DAY_1), you will find the learnings related to cloud computing. Cloud computing is a fundamental concept in DevOps, and it involves leveraging remote servers and services for storing, managing, and processing data.

In the Day 1 folder, you will discover:

- An explanation of what cloud computing is
- Advantages and scope of cloud computing
- Top cloud platform companies
- Features of cloud computing
- Types of cloud computing

Feel free to explore the Day 1 folder to dive deeper into the topic and access additional resources.

## Day 2: Linux Commands and File and Folder Transfer between Local Machine and EC2 using SCP

## Introduction to Linux

In Day 2, we will start by exploring the basics of Linux. Linux is an open-source operating system widely used in the DevOps world. Understanding Linux and its commands is essential for DevOps.

Topics covered in the Introduction to Linux section include:

- Where to run Linux commands
- Examples of popular Linux operating systems

## Importance of Learning Linux and Linux Commands for DevOps Practitioners

Next, we will discuss the significance of learning Linux and Linux commands for DevOps practitioners. As a DevOps professional, having a solid understanding of Linux will empower you to effectively work with various tools and technologies used in the DevOps ecosystem.

## Types of Linux Commands

We will then explore different types of Linux commands. Linux commands are categorized based on their functionality and purpose. Understanding these command types will help you navigate and utilize Linux effectively.

The types of Linux commands we will cover include:

- System Commands
- File Management Commands
- Process Management Commands
- Networking Commands
- Package Management Commands
- Text Processing Commands
- User Management Commands

* File and Folder Transfer between Local Machine and EC2 using SCP 
Make sure to explore each command type and learn how they can be used in different scenarios.

As you progress through Day 2, remember to apply your knowledge from Day 1, as Linux commands and understanding Linux will be essential in infrastructure automation and DevOps practices.

## Day 3: EC2 Instances, Elastic IP, Web Servers, and Bootstrap for EC2

On Day 3 of our DevOps learning journey, we will focus on EC2 instances and explore the concept of Elastic IP, the significance of webservers, and leveraging Bootstrap for EC2.

## What is AWS Elastic IP?

Elastic IP is a static public IP address provided by AWS that you can allocate to your AWS resources. It offers persistence, accessibility, and mapping advantages over dynamic IP addresses.

## Why Create Elastic IP?

In this section, we'll discuss the need for Elastic IP, especially in scenarios where you want to maintain a fixed public IP address for your EC2 instances.

## How to Create an Elastic IP

Learn the step-by-step process to create an Elastic IP address in the AWS EC2 Management Console and associate it with your desired EC2 instance.

## Associating and Disassociating Elastic IP with EC2 Instance

Discover how to associate an Elastic IP with an EC2 instance and disassociate it when necessary. These actions allow you to control the IP address mapping for your instances.

## Releasing Elastic IP with EC2 Instance

Understand the steps involved in releasing an Elastic IP address and when it is recommended to do so to avoid unnecessary charges.

## What is a Web Server?

Learn about web servers and their role in serving web content to users. We'll explore the difference between regular servers and web servers, as well as the process of converting an EC2 instance into a web server.

## Creating a Web Server Using Bootstrap Script

Discover the concept of a Bootstrap script and how it automates the setup and configuration of a web server. We'll provide an example of creating a Linux EC2 machine on AWS using a Bootstrap script.

By exploring these topics, we will further enhance our understanding and skills in the DevOps domain, bringing us closer to becoming proficient DevOps practitioners.

Let's continue our 60 Days DevOps Challenge journey and expand our expertise together!

## Day 4: Placement Groups, Load Balancers, Target Groups, and Launch Templates
On Day 4 of our DevOps learning journey, we will delve into important topics such as Placement Groups, Load Balancers, Target Groups, and Launch Templates. These concepts play a crucial role in optimizing infrastructure, enhancing scalability, and improving the overall performance of our applications.

Make sure to check the Day 4 folder for detailed learnings and resources related to these topics.


## Day 5: AWS EC2 Auto Scaling, AWS Status Check, Automatic Recovery

On Day 5 of our DevOps learning journey, we focused on the following topics:

- AWS EC2 Auto Scaling: We learned how to create an Auto Scaling group with a load balancer in AWS EC2. This involves creating a launch configuration or launch template, setting up a topic in AWS Simple Notification Service (SNS), creating the Auto Scaling group, configuring an Application Load Balancer (ALB), creating a target group, setting up an alarm in CloudWatch, and adding a scaling policy to the Auto Scaling group.

- AWS Status Check: We explored the AWS Status Check feature, which ensures the health and availability of EC2 instances. We learned about system status checks and instance status checks, and how they help monitor the overall system and instance health.

- Automatic Recovery: We discussed automatic recovery in AWS, which is enabled when a system status check failure occurs. We explored how to enable auto recovery for an instance and how AWS automatically attempts to recover the instance in case of a failure.

By understanding these concepts and practices, we gained valuable insights into scaling our EC2 instances, monitoring their health, and ensuring automatic recovery in case of failures.

## Day 6: Snapshots, Amazon Machine Images (AMIs), Scheduled Snapshots, Data Lifecycle Manager, and the Recycle Bin

On Day 6 of our DevOps learning journey, we will continue exploring AWS storage services. We will focus on important topics such as Snapshots, Amazon Machine Images (AMIs), Scheduled Snapshots, Data Lifecycle Manager, and the Recycle Bin. These storage features will enhance our data protection, backup management, automation capabilities, and overall efficiency in managing our AWS infrastructure.

In the Day 6 folder, you will discover:

- Snapshots: Learn how to create point-in-time copies of your block storage data, such as EBS volumes, to protect against accidental deletion and enable data recovery.

- Amazon Machine Images (AMIs): Explore pre-configured templates that contain the necessary software and configurations to launch instances in Amazon EC2. Learn how to create custom AMIs and utilize them for consistent instance deployments.

- Scheduled Snapshots: Discover how to automate the creation of EBS snapshots based on defined schedules using AWS Event Bridge. This ensures regular and consistent backups of your EC2 instance's volumes.

- Data Lifecycle Manager: Simplify the process of managing your data backups with Data Lifecycle Manager. Learn how to automatically create, retain, and delete EBS snapshots based on predefined policies.

- The Recycle Bin: Utilize the Recycle Bin feature in AWS to store and manage deleted EBS snapshots, providing a safety net against accidental data loss and allowing for easy recovery if needed.

Feel free to explore the Day 6 folder to dive deeper into these topics and access additional resources related to AWS storage services.

As you progress through the challenge, make sure to check the corresponding folders for each day to access the specific learnings and resources related to that topic.

Happy learning and enjoy your DevOps journey!