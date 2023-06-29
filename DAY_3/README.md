## Elastic Load Balancer
An Elastic Load Balancer is a service which uniformly distributes network traffic and workloads across multiple servers.

## Types of Load Balancer
• Classic Load Balancer
• Application Load Balancer
• Network Load Balancer
• Gateway Load Balancer

## Classic Load Balancer
A Classic load balancer distributes equally incoming application traffic across multiple EC2 instances in multiple Availability Zones. This increases the fault tolerance of your applications. Elastic Load Balancing detects unhealthy instances and routes traffic only to healthy instances.

The load balancer also monitors the health of its registered targets and ensures that it routes traffic only to healthy targets. When the load balancer detects an unhealthy target, it stops routing traffic to that target. It then resumes routing traffic to that target when it detects that the target is healthy again.

## Classic Load Balancer Terms
**• Response Timeout:** The amount of time to wait when receiving a response from the health check.
**• Interval:** The amount of time between health checks of an individual instance.
**• Unhealthy Threshold:** The number of consecutive failed health checks that must occur before declaring an EC2 instance unhealthy.
**• Healthy Threshold:** The number of consecutive successful health checks that must occur before declaring an EC2 instance healthy.

## Steps to create classic load balancer
• Create Linux EC2 Machine

• Add Bootstrap Script Code in the last for 1st instance
   #!/bin/bash
     sudo su
    yum update -y
    yum install httpd -y
    cd /var/www/html
    echo "LoadBalancer-1" > index.html
    service httpd start
    chkconfig httpd on

• Enable HTTP Port

• Create Second Linux EC2 Machine

• Bootstrap Script Code for 2nd instance
   #!/bin/bash
    sudo su
    yum update -y
    yum install httpd -y
    cd /var/www/html
    echo "LoadBalancer-2" > index.html
    service httpd start
    chkconfig httpd on

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


