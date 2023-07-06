# DAY 4 OF DEVOPS LEARNING 

Building upon our previous knowledge gained during the first three days of our 60 Days DevOps Challenge, where we explored cloud computing, the benefits of Linux in DevOps, and concepts related to EC2 instances, we are now ready to expand our understanding further. In Day 4, we will focus on important topics such as Placement Groups, Load Balancers, Target Groups, and Launch Templates. These concepts play a crucial role in optimizing infrastructure, enhancing scalability, and improving the overall performance of our applications.

## Linking with Previous Learning

Before we dive into the specifics of Day 4's topics, let's quickly recap what we have learned so far:

- **Day 1**: We started our DevOps journey by understanding the fundamentals of cloud computing. We explored the key concepts of cloud computing, including Infrastructure-as-a-Service (IaaS), Platform-as-a-Service (PaaS), and Software-as-a-Service (SaaS). Additionally, we gained insights into the benefits of leveraging cloud services for DevOps practices, such as scalability, cost-efficiency, and flexibility.

- **Day 2**: Building upon our cloud computing knowledge, we focused on the significance of Linux in the DevOps domain. We learned about the advantages of Linux as an operating system for DevOps practices, its command-line interface (CLI), package management, and the importance of scripting in automating tasks. This knowledge laid the foundation for efficient management and administration of our DevOps infrastructure.

- **Day 3**: Expanding further into the realm of EC2 instances, we delved into Elastic IP, webservers, and Bootstrap for EC2. We understood the role of Elastic IP in providing a static public IP address to our AWS resources, ensuring persistence and accessibility. We also explored the concept of webservers and how to configure an EC2 instance to serve web pages. Finally, we learned about Bootstrap scripts and their role in automating the setup and configuration of EC2 instances.

Now that we have established a strong foundation in cloud computing, Linux, and EC2 instances, let's proceed to explore the topics for Day 4.

# Placement Groups
Placement Groups are a powerful feature provided by AWS to control the placement of EC2 instances within the underlying infrastructure.
When we launch a new EC2 instance, the EC2 service attempts to place the instance in such a way that all of your instances are spread out across underlying hardware to minimize failures. No Charges to Create Placement Groups.

* Types of Placement Groups
There are three types of Placement Groups in AWS:

## 1. Cluster Placement Group
A Cluster Placement Group is a setting that instructs AWS to launch EC2 instances within the same "rack" in an Amazon Data Center. In this context, a rack refers to a physical grouping of servers. When you specify the 'Cluster' placement group, all the instances will be launched in the same rack within the same availability zone (AZ).

To visualize, think of an Amazon Data Center with thousands of servers organized into different racks. When you use the 'Cluster' placement group, all the instances you launch will be placed within the same rack, ensuring they are physically close to each other. This proximity allows for excellent network performance, with minimal delays or latency

*Use Cases*: Cluster Placement Groups are ideal for applications that require low-latency and high-throughput communication, such as big data processing or applications with strict performance requirements.

Great network performance with low latency: Instances in a Cluster Placement Group benefit from high-speed network connectivity, with a bandwidth of 10Gbps between them. This enables fast and efficient communication.

* To create a Cluster Placement Group:

1. Go to the EC2 service in the AWS Management Console.
2. Click on "Create Placement Group."
3. Enter a name for the placement group.
4. Select the "Cluster" placement strategy.
5. Click on "Create Group."

## 2. Spread Placement Group
A Spread Placement Group is designed to distribute your highly available application across multiple data centers. It ensures that instances are placed in different availability zones (AZs) and on different physical racks within the same AZ.

To visualize, imagine you have a highly available application that needs to be resilient to failures. By using a Spread Placement Group, your instances will be distributed across multiple data centers, with each instance placed on different physical racks and in different AZs. This ensures that even if there is a failure in one data center or rack, your application will continue to run smoothly.

Use Cases: Spread Placement Groups are suitable for applications that require high availability and need to be isolated from failures in other instances.

* To create a Spread Placement Group:

1. Go to the EC2 service in the AWS Management Console.
2. Click on "Create Placement Group."
3. Enter a name for the placement group.
4. Select the "Spread" placement strategy.
5. Select the desired spread level, such as "Rack."
6. Click on "Create Group."

## 3. Partition Placement Group
A Partition Placement Group enables you to allocate instances to specific partitions, with each partition representing a rack in the AWS infrastructure. Each partition is isolated, so failures in one partition do not impact others.

Use Cases: Partition Placement Groups are well-suited for applications that process massive amounts of data, such as Apache Hadoop clusters.

* To create a Partition Placement Group:

1. Go to the EC2 service in the AWS Management Console.
2. Click on "Create Placement Group."
3. Enter a name for the placement group.
4. Select the "Partition" placement strategy.
5. Specify the desired number of partitions.
6. Click on "Create Group."

* To make use of a Placement Group for your EC2 instances, follow these steps:

Create an EC2 instance as usual.
In the advanced details section, select the appropriate Placement Group based on your requirements.
Launch the instance.
By utilizing Placement Groups, you can optimize the performance and reliability of your EC2 instances based on your specific application needs.

Note: It's important to be aware that while Placement Groups offer benefits in terms of performance and availability, they are limited to a single AWS region.



# Elastic Load Balancer
An Elastic Load Balancer (ELB) is a service provided by Amazon Web Services (AWS) that acts as a traffic cop for your web applications. Imagine you have a popular website, and lots of users are trying to access it at the same time. Without a load balancer, all the requests from those users would go to a single server, which could potentially overwhelm it and make the website slow or even crash.

The load balancer solves this problem by distributing the incoming traffic across multiple servers in a balanced way. It acts as a middleman between the users and the servers, receiving all the incoming requests and sending them to different servers based on their availability and capacity. This ensures that the workload is spread evenly, preventing any one server from becoming overloaded.

The load balancer also monitors the health of the servers and automatically removes any servers that are not responding or are experiencing issues. It can detect when a server is under too much load and divert traffic away from it, ensuring that the application remains available and responsive to users.

In simpler terms, an Elastic Load Balancer helps keep your website running smoothly by distributing the traffic across multiple servers, preventing any single server from becoming overwhelmed. It improves the performance, scalability, and availability of your web applications.

## Types of Load Balancer
• Classic Load Balancer <br>
• Application Load Balancer<br>
• Network Load Balancer<br>
• Gateway Load Balancer<br>

## Classic Load Balancer
A Classic load balancer distributes equally incoming application traffic across multiple EC2 instances in multiple Availability Zones. This increases the fault tolerance of your applications. Elastic Load Balancing detects unhealthy instances and routes traffic only to healthy instances.

The load balancer also monitors the health of its registered targets and ensures that it routes traffic only to healthy targets. When the load balancer detects an unhealthy target, it stops routing traffic to that target. It then resumes routing traffic to that target when it detects that the target is healthy again.

## Classic Load Balancer Terms
**• Response Timeout:** The amount of time to wait when receiving a response from the health check.<br>
**• Interval:** The amount of time between health checks of an individual instance.<br>
**• Unhealthy Threshold:** The number of consecutive failed health checks that must occur before declaring an EC2 instance unhealthy.<br>
**• Healthy Threshold:** The number of consecutive successful health checks that must occur before declaring an EC2 instance healthy.<br>

## Steps to create classic load balancer
• Create Linux EC2 Machine

• Add Bootstrap Script Code in the last for 1st instance<br>
  #!/bin/bash<br>
  sudo su<br>
  yum update -y<br>
  yum install httpd -y<br>
  cd /var/www/html<br>
  echo "LoadBalancer-1" > index.html<br>
  service httpd start<br>
  chkconfig httpd on<br>

• Enable HTTP Port

• Create Second Linux EC2 Machine

• Bootstrap Script Code for 2nd instance<br>
    #!/bin/bash<br>
    sudo su<br>
    yum update -y<br>
    yum install httpd -y<br>
    cd /var/www/html<br>
    echo "LoadBalancer-2" > index.html<br>
    service httpd start<br>
    chkconfig httpd on<br>

• Enable HTTP Port

• Go to Load balancer

• Click on Create for Classic Load Balancer

• Define Load Balancer Name

• Assign Security Group (select same security group which you have selected while creating EC2 machine)

• Configure Security Settings

• Configure Health Check (Important)

• Enter Response timeout

• Enter Interval

• Enter Unhealthy threshold

• Enter healthy threshold

• Add EC2 Instances

• Review

• Click on Create

• Copy DNS Name & Paste in the browser


**Note**- Now you are able to access your two machine with single DNS and in the case of classic load balancer incoming traffic with route equally to both EC2 machines.

## Application Load Balancer
Application Load Balancer routing traffic to targets based on the content of the request.

## Application Load Balancer Terms
**• Listener:** A listener is a process that checks for connection requests.

**• Response Timeout:** The amount of time to wait when receiving a response from the health check.

**• Interval:** The amount of time between health checks of an individual instance.

**• Unhealthy Threshold:** The number of consecutive failed health checks that must occur before declaring an EC2 instance unhealthy.

**• Healthy Threshold:** The number of consecutive successful health checks that must occur before declaring an EC2 instance healthy.

## Steps to create Application load balancer
• Create Linux EC2 Machine

• Add Bootstrap Script Code in the last for 1st instance<br>
  #!/bin/bash <br>
  sudo su<br>
  yum update -y<br>
  yum install httpd -y<br>
  cd /var/www/html<br>
  echo "AmazonWebservices" > index.html<br>
  service httpd start<br>
  chkconfig httpd on<br>

• Connect to the machine using putty

• Switch User<br>
  sudo su

• Switch to html folder<br>
  cd /var/www/html

• Create Directory<br>
  mkdir custom

• Switch to new directory<br>
  cd custom

• Create web page in the directory<br>
  echo "Google Drive" > index.html

• Now check the public IP/custom in the browser

• Create Second Linux EC2 Machine

• Add Bootstrap Script Code in the last for 2nd instance<br> 
    #!/bin/bash <br>
    sudo su<br>
    yum update -y<br>
    yum install httpd -y<br>
    cd /var/www/html<br>
    echo "AmazonWebservices" > index.html<br>
    service httpd start<br>
    chkconfig httpd on<br>

• Connect machine using putty

• Switch User<br>
  sudo su

• Switch to html folder<br>
  cd /var/www/html

• Create Directory<br>
  mkdir image

• Switch to new directory<br>
  cd image

• Create web page in the directory
  echo "Google Image" > index.html

• Now check the public IP/image in the browser

# Network Load Balancer

A Network Load Balancer routes traffic to targets based on the port number. It has the capability to respond to millions of requests every second, making it suitable for high-performance applications.

* Create EC2 Instances 

1. Create the first Linux EC2 machine.
   - Bootstrap Script Code:
  #!/bin/bash
  sudo su
  yum update -y
  yum install httpd -y
  cd /var/www/html
  echo "LoadBalancer-1" > index.html
  service httpd start
  chkconfig httpd on

Enable the type as HTTP.

2. Create the second Linux EC2 machine.
   - Bootstrap Script Code:
   #!/bin/bash
   sudo su
   yum update -y
   yum install httpd -y
   cd /var/www/html
   echo "LoadBalancer-2" > index.html
   service httpd start
   chkconfig httpd on

Enable the type as HTTP.
- Enable the Custom TCP type and change the port range to 8080.

3. Check the Public IP Address for both machines.

4. Add ":8080" port number for the second EC2 machine.

5. Connect to the second EC2 machine using Putty or terminal.

6. Change the user to `sudo su`.

7. Change the folder to `/etc/httpd/conf`.

8. Edit the `httpd.conf` file using the command `vi httpd.conf`.

9. Convert the file into insert mode by pressing `i`.

10. Change the `Listen` directive to `8080`.

11. Save the file by pressing `ESC` followed by `:wq`.

12. Restart the server using the command `service httpd restart`.

* Create Target Group

1. Click on "Create target group".
2. Enter the name of the target group.
3. Change the protocol to TCP and set the port number to 80 for the first machine.
4. Click on "Next".
5. Add the first machine as a target.
6. Click on "Create target group".
7. Create a target group for the second machine and enter the port number as 8080.

* Create Network Load Balancer

1. Click on "Create" for Network Load Balancer.
2. Enter the name of the load balancer.
3. Map all the subnets.
4. Select the listener and target group.
5. Click on "Create load balancer".

* Configure Load Balancer

1. Go to the Listeners tab.
2. Click on "Add Listener".
3. Change the port number to 8080.
4. Add an action to forward to the second machine.
5. Click on "Add Listener".

* Access Load Balancer

Copy the DNS Name of the load balancer and use it to access your application. The load balancer will distribute traffic based on the configured rules.

Please note that this is a simplified explanation, and it's recommended to refer to the AWS documentation for detailed instructions and best practices when creating a Network Load Balancer.


# Gateway Load Balancer

A Gateway Load Balancer is a scalable and highly available service that enables you to deploy and manage third-party virtual appliances such as firewalls, intrusion detection and prevention systems, and deep packet inspection systems. It allows you to protect and inspect inbound and outbound traffic at the network layer (Layer 3).

## Prerequisites

- Before setting up a Gateway Load Balancer, ensure that you have deployed the necessary virtual appliances and configured their settings.

## Create Gateway Load Balancer

1. Open the AWS Management Console and go to the Amazon VPC service.

2. Click on "Gateway Load Balancers" in the navigation pane.

3. Click on "Create Gateway Load Balancer".

4. Provide a name for your load balancer.

5. Select the VPC where you want to deploy the load balancer.

6. Configure the security group settings to allow inbound and outbound traffic as required for your virtual appliances.

7. Add the virtual appliances to the load balancer by specifying their IP addresses or DNS names.

8. Review the settings and click on "Create Load Balancer".

9. Once the load balancer is created, note down its DNS name for accessing your virtual appliances.

## Update Route Tables

1. Go to the Amazon VPC service in the AWS Management Console.

2. Click on "Route Tables" in the navigation pane.

3. Select the route table associated with the subnet where your virtual appliances are deployed.

4. Add a new route that directs traffic to the Gateway Load Balancer. Set the destination IP range as "0.0.0.0/0" and specify the Gateway Load Balancer as the target.

5. Save the changes to update the route table.

## Access Virtual Appliances

To access the virtual appliances deployed behind the Gateway Load Balancer, use the DNS name of the load balancer. The load balancer will route traffic to the appropriate virtual appliance based on the configured rules.

Please note that this is a simplified explanation, and it's recommended to refer to the AWS documentation for detailed instructions and best practices when working with Gateway Load Balancers.


# Launch Template

A Launch Template is a convenient way to save and manage your EC2 instance configurations. It allows you to define a set of parameters for launching instances, including the AMI, instance type, security groups, and more. Launch Templates provide a flexible and efficient way to create consistent instances with predefined configurations.

## Create Launch Template

1. Open the AWS Management Console and go to the EC2 service.

2. Click on "Launch Templates" in the navigation pane.

3. Click on "Create launch template".

4. Provide a name and description for your launch template.

5. Configure the instance settings, such as the AMI, instance type, key pair, and security groups.

6. Customize the advanced options, including user data, block device mappings, and instance metadata.

7. Set the networking options, such as VPC, subnet, and security groups.

8. Review the configuration and click on "Create launch template".

## Launch Instances from the Launch Template

1. Go to the "Launch Templates" section in the EC2 service.

2. Select the launch template you want to use.

3. Click on "Actions" and choose "Launch instances".

4. Configure the number of instances you want to launch and other instance details.

5. Review the configuration and click on "Launch instances".

6. The instances will be launched based on the settings defined in the launch template.

## Update Launch Template

1. Go to the "Launch Templates" section in the EC2 service.

2. Select the launch template you want to update.

3. Click on "Actions" and choose "Create new version".

4. Modify the desired settings in the new version of the launch template.

5. Review the configuration and click on "Create launch template version".

6. The new version of the launch template will be created.

## Delete Launch Template

1. Go to the "Launch Templates" section in the EC2 service.

2. Select the launch template you want to delete.

3. Click on "Actions" and choose "Delete launch template".

4. Confirm the deletion when prompted.

Please note that launch templates provide a convenient way to manage and launch instances with predefined configurations. It's recommended to refer to the AWS documentation for detailed instructions and best practices when working with launch templates.












