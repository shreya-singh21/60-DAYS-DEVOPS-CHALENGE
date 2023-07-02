# DAY 3 OF DEVOPS LEARNING

Building upon our previous knowledge of cloud computing from Day 1 and exploring the benefits of Linux in DevOps on Day 2, we are now ready to delve into more concepts related to EC2 instances.  In Day 3, we will focus on learning about Elastic IP, understanding the significance of webservers, and leveraging Bootstrap for EC2. These topics will further enhance our understanding and skills in the DevOps domain. Let's continue our 60 Days DevOps Challenge journey and expand our expertise together!

## What is AWS Elastic IP?

Elastic IP is a static public IP address provided by AWS that you can allocate to your AWS resources, such as EC2 instances, NAT gateways, and load balancers. Here are the details regarding Elastic IP and its usage

## Why Create Elastic IP?
* Every ec2 instance have public and private ip address then what is the need of Elastic IP

The Elastic IP (EIP) feature in AWS provides a static public IP address that offers several benefits:

- Persistence: By default, when you stop or start an EC2 instance, it gets assigned a new public IP address each time. This can be problematic if you've linked your IP address to a domain because you would need to update the IP address everywhere it's mapped whenever you stop or restart the instance. However, by using an Elastic IP, you can ensure that your instance maintains a fixed public IP address even after stopping or starting it. This means you won't have to change the IP address wherever it's used, making it more convenient and reliable.

- Accessibility: Elastic IP allows you to easily connect to your EC2 instance from the internet, as you can use the static IP address to access your server instead of relying on dynamic IPs.

- Mapping: Elastic IP can be associated with instances in a Virtual Private Cloud (VPC) or with instances in EC2-Classic. It provides a way to map your instance to a fixed IP address.

## Disadvantages of AWS Elastic IP

- **Limited Availability**: There is a limit on the number of Elastic IPs you can allocate per AWS account.
- **Cost**: Elastic IP addresses are free to use when associated with a running instance. However, it's important to note that if you don't utilize the Elastic IP properly, charges may apply. As a best practice, it is recommended to delete your Elastic IP address after you no longer need it. Even if you delete your EC2 instance, you may still incur charges for the Elastic IP. Simply disassociating the Elastic IP does not prevent billing. Therefore, it is always advisable to delete the Elastic IP address if you are not actively using it.

## How to Create an Elastic IP

To create an Elastic IP, follow these steps:
1. Open the EC2 Management Console.
2. In the navigation page, click "Elastic IPs".
3. Click the "Allocate new address" button.
4. Optionally, specify the specific address pool, then click "Allocate".
5. Once the allocation is successful, you can associate the Elastic IP with your desired EC2 instance.

## Associating and Disassociating Elastic IP with EC2 Instance

To associate an Elastic IP with an EC2 instance, follow these steps:
1. Open the EC2 Management Console in your AWS account.
2. In the navigation pane, click on "Elastic IPs" under the "Network & Security" section.
3. Click on the "Allocate new address" button to create a new Elastic IP.
4. Confirm the allocation by clicking on the "Allocate" button.
5. Once the Elastic IP is created, select it from the list of Elastic IPs.
6. Click on the "Actions" dropdown menu and choose "Associate IP address".
7. In the "Associate Elastic IP address" dialog box, select the EC2 instance you want to associate the Elastic IP with from the dropdown menu.
8. Optionally, you can specify the private IP address of the instance if you want to associate the Elastic IP with a specific private IP.
9. Click on the "Associate" button to complete the association.
After the association is successful, the Elastic IP address will be associated with your chosen EC2 instance, and it will remain associated even if you stop and start the instance. You can use this Elastic IP address to access your EC2 instance from the internet.

To disassociate an Elastic IP from an EC2 instance, follow these steps:
1. Open the EC2 Management Console in your AWS account.
2. In the navigation pane, click on "Elastic IPs" under the "Network & Security" section.
3. Select the Elastic IP address that you want to dissociate from the EC2 instance.
4. Click on the "Actions" dropdown menu and choose "Disassociate IP address".
5. Confirm the disassociation by clicking on the "Disassociate" button.
After the disassociation is successful, the Elastic IP address will no longer be associated with the EC2 instance. The EC2 instance will revert to using its default public IP address if it has one. You can choose to associate the Elastic IP with another EC2 instance or release it if you no longer need it

## Releasing Elastic IP with EC2 Instance
1. Open the EC2 Management Console in your AWS account.
2. In the navigation pane, click on "Elastic IPs" under the "Network & Security" section.
3. Select the Elastic IP address that you want to release.
4. Click on the "Actions" dropdown menu and choose "Release addresses".
5. Confirm the release by clicking on the "Release" button

## What is a Web Server?

A web server is a program that uses HTTP (Hypertext Transfer Protocol) to serve files from web pages to users in response to their requests.

**Example of Web Servers:**
- Apache HTTP Server
- Internet Information Services (IIS)
- NGINX
- HTTPD by Apache

A regular server, such as the computer you use every day, is a versatile device that can handle a variety of tasks. It can store files, run software applications, manage databases, and perform other functions based on its configuration.

In contrast, a web server is a specialized type of server specifically designed to host websites and serve web content to users. While both regular servers and web servers can perform similar tasks, a web server is optimized for handling website-related processes efficiently.

When you create an EC2 instance (virtual server) on a cloud platform like Amazon Web Services (AWS), you start with a basic server configuration. Initially, the server is not specifically set up as a web server. However, you can transform it into a web server by following a few key steps:

1. **Installing the Operating System:** Begin by installing a suitable operating system on the server. Popular choices for web servers are Linux distributions such as Ubuntu, CentOS, or Debian.

2. **Installing Web Server Software:** Next, install web server software on the server. Two common options are Apache HTTP Server and Nginx. These software packages enable the server to handle incoming web requests and serve web pages.

3. **Configuring the Web Server:** After installing the web server software, configure it to meet your needs. This involves setting up virtual hosts, which allow multiple websites to be hosted on a single server. Additionally, you'll define server directories, configure security settings, and optimize performance.

4. **Deploying Website Files:** Once the web server is configured, deploy your website files to the server. This typically involves transferring HTML, CSS, JavaScript, images, and other resources from your local machine to the server. You can use methods like FTP, SCP, or Git for file transfer.

5. **Testing and Maintenance:** After deploying the website files, thoroughly test the web server to ensure it properly serves the web pages. Make any necessary adjustments, such as configuring domain names, setting up SSL certificates for secure connections (HTTPS), and optimizing server performance.

Following these steps, you can convert a regular server (such as an EC2 instance) into a web server capable of hosting and serving websites.

## I am going to show an example of how you can make your EC2 machine a web server using HTTPD by Apache.

### Step 1:Create Linux EC2 Machine
- Launch an EC2 instance on the AWS platform.
- Choose a suitable Linux AMI (Amazon Machine Image) like Ubuntu, CentOS, or Amazon Linux.

### Connect to the Linux EC2 Machine
- Use an SSH client (such as PuTTY) to connect to the EC2 instance or you can connect with windows powershell, or for ubuntu and mac you can connect with terminal.
- Enter the SSH key and the public IP address of the instance.

* Switch User to root
sudo su
### Step 2: Update the YUM Repository
sudo yum update -y

### Step 2: Install Web Package
sudo yum install httpd -y

### Move to the html Directory
cd /var/www/html

### Create a Web Page
echo "Hi this is a web page for testing webserver" > index.html

### Start the Web Package
service httpd start
chkconfig httpd on

### Now, our Linux machine is a web server.
### Copy the Public IP & Paste in the Web Browser
- Copy the public IP address of the EC2 instance.
- Paste the IP address in a web browser.

### If Security Group Has Not Enabled HTTP Port
- Select your security group associated with the EC2 instance.
- Edit inbound rules.
- Click on "Add Rule."
- Change the type to "HTTP" and the source to "Anywhere IPV4."
- Click on "Save rules."
- Now, refresh the web browser.

# Bootstrap Script
A Bootstrap script, in the context of computing, refers to a script or a set of instructions that is executed during the bootstrapping process of a system or application. Bootstrapping is the initial setup or initialization phase where essential components or configurations are prepared to enable the system or application to run.

* Bootstrapping allows us to write and put a startup script while launching an EC2 Instance so that it execute      automatically as soon as the instance launch.

The Bootstrap script typically performs tasks such as:

- Installing necessary software packages or dependencies.
- Configuring system settings and parameters.
- Setting up environment variables.
- Creating directories or file structures.
- Initializing databases or data storage.
- Starting required services or processes.
- Running initial setup or configuration scripts.

In the context of cloud computing or server provisioning, a Bootstrap script is often used to automate the setup of virtual machines or instances. When launching a new virtual machine or instance, the Bootstrap script is executed to perform the necessary configurations and installations required for the system or application to run correctly.

Bootstrap scripts can be written in various scripting languages such as Bash, PowerShell, Python, or cloud-specific configuration management tools like CloudFormation, Terraform, or Ansible. These scripts can be customized to meet specific requirements and automate the deployment and configuration process, saving time and effort in manual setup.

Overall, a Bootstrap script plays a crucial role in the initial setup and configuration of systems and applications, allowing for efficient and automated provisioning of resources.

# Creating a Web Server Using Bootstrap Script

In this example, we will create a Linux EC2 machine on Amazon Web Services (AWS) using a Bootstrap script. The Bootstrap script automates the installation and configuration of the web server.

Follow the steps below to create the server:

1. Go to Aws ec2 dashboard provide a name for your EC2 machine.

2. Select AMI (Amazon Linux): Choose the Amazon Machine Image (AMI) for the Linux distribution.

3. Choose an Instance Type: Select the appropriate instance type based on your requirements.

4. Select Key pair or Create new key pair: Choose an existing key pair or create a new one for SSH access.

5. Enable SSH Port & HTTP Port: Ensure that the SSH port (22) and HTTP port (80) are open in the security group.

6. Select Configure Storage: Configure the storage settings based on your needs.

7. Click on Advanced Details: In the user data section, add the Bootstrap script.

8. Add the following code to the Bootstrap script:
  ```bash
        #!/bin/bash
        sudo su
        yum update -y
        yum install httpd -y
        cd /var/www/html
        echo "Hi, this is a web page for testing the web server" > index.html
        service httpd start
        chkconfig httpd on


Copy the Public IP and paste it into a web browser to access the web page served by the EC2 machine.
By following these steps and executing the Bootstrap script, you can create a Linux EC2 machine and automatically install and configure the web server. The web page "Hi, this is a web page for testing the web server" will be available on the Public IP of the EC2 machine.

Please note that the above steps assume you are using AWS EC2, but the concept of using a Bootstrap script can be applied to other cloud platforms or server provisioning scenarios as well.