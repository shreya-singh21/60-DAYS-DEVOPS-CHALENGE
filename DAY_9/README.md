## VIRTUAL PRIVATE CLOUD

Till the time whatever EC2 created we created in default VPC. A default VPC (Virtual Private Cloud) is a pre-configured VPC that is automatically created in each AWS region when you sign up for an AWS account. 

Default VPC is designed to provide a default networking environment for new AWS users, making it easier for them to launch resources and start using AWS services without the need for additional configuration.

But it is often recommended to create custom VPCs with specific network configurations tailored to your application requirements.

Custom VPCs offer more control over security, network architecture, and resource isolation, making them suitable for production environments and multi-tiered applications.

Custom VPC in AWS offers a private, secure, and customizable networking environment, providing the foundation for building and deploying applications with enhanced security, scalability, and connectivity. 

It is logically isolated from other virtual networks in the AWS Cloud. You can launch your AWS resources, such as Amazon EC2 instances, into your VPC.

A Custom virtual private cloud (VPC) is a virtual network dedicated to your AWS account.

**VPC is like under my AWS region I have taken my private space and I have complete control over that private space so that private space will be my VPC.**



## Key Features of AWS VPC

1. VPC allows the user to select IP address range, create subnets, and configure route tables, network gateways, and security settings.

2. VPC allows VPC Peering connections with other VPC within the same or different AWS accounts.

3. It provides a feature of security such that the data stored in Amazon S3 can only be accessed from within your Amazon VPC.

4. We can resize the VPC.

5. Max VPC is 5 Per Region. We can increase this limit so that you can have 100s of VPCs per Region.

6. We can create 200 Subnets in one VPC & 1000 Subnets in one region


## VPC - SIZING

When you create a VPC, you must specify an IPv4 CIDR block for the VPC. The allowed block size is between a /16 netmask (65,536 IP addresses) and /28 netmask (16 IP addresses). After you've created your VPC, you can associate additional IPv4 CIDR blocks with the VPC.

VPC needs a set of IP addresses in the form of a Classless Inter-Domain Routing (CIDR) block. For example: the CIDR 172.16.0.0/16 includes all addresses from 172.16.0.0 to172.16.255.255 — a total of 65,536 addresses. 16 is the netmask.

• As IPV4 is 32 bit so /16 means , 32-16=16 and so 2^16=65,536 IP addresses

• Similarly for /28 means, 32-28= 4 and so 2^4=16 IP addresses.

• Block sizes must be between a /16 netmask and /28 netmask.

• Minimum Size is /28 (16 IP Address)

• Maximum Size is /16 (65536 IP Address)


**Let's create VPC**

1. Go to VPC.

2. Give the VPC name.

3. Enter IPV4 CIDR <br/>
   ex- 10.0.0.0/16

4. Create VPC.


## VPC - SUBNET

In a Virtual Private Cloud (VPC) in Amazon Web Services (AWS), a subnet is a segmented portion of the VPC's IP address range. It is a way to partition the VPC into smaller, more manageable network segments.

Each subnet is associated with a specific CIDR (Classless Inter-Domain Routing) block, which is a range of IP addresses. Subnets within a VPC can be of different sizes and are used to isolate and organize resources within the VPC. Subnets play a crucial role in enabling the isolation and control of network traffic between different groups of resources.

**Earlier we were dividing aws region into parts called VPC**<br/>
**Now we need to divide the VPC into small-small parts called subnets**

**Subnets can be categorized into two main types:**

**Public Subnet**: A public subnet is a subnet that has a route to the internet through an Internet Gateway (IGW). Resources placed in a public subnet can have public IP addresses and are accessible directly from the internet. Common examples of resources placed in a public subnet are web servers, load balancers, and Bastion hosts.

**Private Subnet**: A private subnet is a subnet that does not have a direct route to the internet. Resources placed in a private subnet cannot be accessed directly from the internet. They can only communicate with the internet through a Network Address Translation (NAT) Gateway, a NAT instance, or through a VPC peering connection to a public subnet. Private subnets are often used to host backend servers, databases, and other internal resources that do not require direct internet access.


**By default when we create subnet under VPC it will be created as private subnet**

**For Subnet we need to give IP address range**

**Can we give any IP to subnet?**<br/>
No, the ip address range which we have given to VPC so In that range only we need to give to subnet.<br/>

We need to give Ip address in this 10.0.0.0/16 range <br/>

The first two number in Ip address will be same 10.0.1.0/24<br/>

/16 means 65536 IP address range we are assigning to subnet. So we cannot give huge IP range to subnets.<br/>

Instead of /16 we'll give /24 <br/>

/24 means 32-24= 8 and 2^8= 256 IP Address, we can give to **Private subnet**.

It means from 65536 - 256 = 65280 IP Addresses are remaining.

We can create multiple subnet and assign IP addresses to them.

10.0.2.0/24 --256 we can give to **Public subnet**

If we give 256 IP address to subnet then AWS will reserve 5 IP address out of 256 from each subnet so 251 ip address we have means 251 ec2 machine we can create in private subnet.

AWS Reserve 5 IP Addresses (First 4 & Last 1) in each subnet

• These 5 IP Addresses are not available for use and can’t be assigned to an EC2 Instance. For example, if your VPC has a CIDR of 192.168.0.0/16, one of your subnets may have a CIDR of 192.168.100.0/24. This range covers 192.168.100.0–192.168.100.255, which yields a total of 256 addresses.

• First four addresses: 192.168.100.0 –192.168.100.3 & Last IP Address: 192.168.100.255

• 192.168.100.0: Network address

• 192.168.100.1: Reserved by AWS for the VPC router.

• 192.168.100.2: Reserved by AWS for mapping to AWS provided
DNS.

• 192.168.100.3: For Future Use

• 192.168.100.255: Network broadcast address. We do not support broadcast in a VPC, therefore we reserve this address.


**Let's create subnet under VPC**

1. Click on subnets

2. We are able to see all the default subnets

3. Click on create subnet. For ex- Private Subnet

4. Select the VPC in which we want to create the subnet

5. Enter subnet name, Select availability zone & Enter IPV4 CIDR Block.

6. Click on Create subnet

7. Create One More Subnet with Public Subnet name in other availability zone.

**While creating subnets did we mentioned anything that define public subnet or private subnet?**
**By deafault all subnet are private subnets**

**Make Subnet as Public**

1. Choose any subnet that you want to make public subnet if you have created multiple subnet .

2. Go to action

3. Click on edit Subnet setting.

4. click on enable auto assign public IPv4 address.

Now under this subnet whatever EC2 machine will create will automatically get public access.

**NOTE** 
When we create a subnet and launch an EC2 machine within that subnet, the EC2 instance does not have internet connectivity by default. To enable internet connectivity for the EC2 instance, we need to perform one more step. This step involves creating an Internet Gateway, which allows the EC2 instance to access the internet and be publicly reachable.

When we create a subnet in AWS, it is like a private network within our Virtual Private Cloud (VPC). By default, instances within the subnet cannot access the internet, and the internet cannot reach them directly.

To enable internet connectivity for an EC2 instance within the subnet, we need to create an Internet Gateway and attach it to our VPC. The Internet Gateway acts as a bridge between your VPC and the internet.

Once the Internet Gateway is attached, the EC2 instance can send and receive data over the internet, making it publicly accessible and allowing you to connect to it from the internet.

So, creating a subnet alone is not enough to make an EC2 instance publicly accessible. We also need to create an Internet Gateway and associate it with your VPC to enable internet connectivity for our EC2 instance.

## VPC - INTERNET GATEWAY

Component that allows communication between our VPC and the internet.

By default to our VPC don't have internet connectivity.

With the help of internet gateway our public subnet will get public internet


**Let's create internet gateway for VPC**

1. Go to internet gateway.

2. Give the name of internet gateway

3. create internet gateway

After creation of internet gateway will get popup saying that "Attach to a VPC". Click on that popup.

**Now we have to attach Internet Gateway to public subnet. for that we use Route Table**


## VPC - ROUTE TABLE

In AWS Virtual Private Cloud (VPC), a route table is a fundamental component that controls the routing of network traffic between different subnets within the VPC and to the internet. It acts as a set of rules, determining where the traffic should be directed based on its destination.

1. Click on route table

2. You have find two route tables<br/>
   one route table we are getting my defalut from AWS beacuse we have deaflut VPC <br/>
   second route table you will find that it is linked with your VPC but we haven't created it. When we creates VPC by defalut AWS will create a default route tabel for our VPC. If we want to use we can sue it but we'll another route table.

3.  Give the name of route table

4. Select your VPC

5. Click on create route table.

6. Now attach this route table to your public subnet.

7. Select route table<br/>
   Go to Action<br/>
   Edit Subnet Association<br/>
   Here you find your Public Subnet as  well as Private Subnet<br/>
   Click on Public Subnet<br/>
   Save Association

8. Now attach with Internet Gateway<br/>
   To attaching with Internet Gateway we need to provide two things<br/>

   • Destination<br/>
   • Target

9. Select route table<br/>
   Go to Action<br/>
   Edit routes<br/>
   Click on add routes<br/>
   Select Internet Gateway as target <br/>
   Give 0.0.0.0 as destination. 0.0.0.0 means open to all.<br>
   Save route.


Now our Subnet become a public subnet.


**Create EC2 Instance - Public Subnet**

1. Go to EC2

2. Give the name of instance.

3. Select Linux OS.

4. Select keypair.

5. In the Network Settings. Click on Edit.

6. Select our own VPC

7. Select Public Subnet.

8. Auto Assign will be enable for our Public Subnet.

9. Create Security Group and Enable SSH and HTTP port.

10. In advanced option give bootstarp script<br/>
    #!/bin/bash<br/>
    sudo su<br/>
    yum update<br/>
    yum install httpd<br/>
    cd /var/www/html<br/>
    echo "AmazonWebservices" > index.html<br/>
    service httpd start<br/>
    chkconfig httpd on <br/>

11. Launch Instance


Go to EC2. Click on istance and check public IP and private IP<br/>
You will get dynamic Public IP because you have mentioned anywhere in Security Group and Private IP will be given in the range.

**Create EC2 Instance - Private Subnet**

In this Private Subnet will create database in EC2 machine and will link with Public Subnet EC2 machines not from any part of the world.Public Subnet EC2 machines can only access

1. Go to EC2

2. Give the name of instance.

3. Select Linux OS.

4. Select keypair.

5. In the Network Settings. Click on Edit.

6. Select our own VPC

7. Select Private Subnet.

8. Auto Assign will be disable for our Priate Subnet.

9. Create Security Group and Enable MYSQL/Aurora. <br/>
   MYSQL/Aurora are database.

10. To access this databse we will give "custom" instead of Anywhere because we want to access this database from public subnet instance. Whatever the instance in public subnet can connect to database but other than public subnet instance no one can connect to database. 

11. Mention this 10.0.2.0/24 IP of Public Subnet in MYSQL/Aurora database . 

12. To connect Private subnet we need to take help of Bastion Server.We need to enable ssh and give bastion server private IP address on private subnet.

12. Launch Instance.

**Note**- 1. For Database in private subnet we have given Public Subnet Ip so that EC2 instances in public subnet can connect to database.<br/>
          2. To connect private subnet instances we have given bastion server private IP.


Go to EC2. Click on istance and check public IP and private IP<br/>
You will not get Public IP because you have  not mentioned anywhere in Security Group and Private IP will be given in the range.


## BASTON SERVER

A bastion host is a server whose purpose is to provide access to a private network from an external network, such as the Internet.

**Note**: Bastion server is nothing but normal EC2 Machine.

Suppose a person who wants to connect our Private Subnet EC2 machine. Can we connect directly?<br/>
No, we cannot connect directly because we have not given public Ip address.

How can we connect to this machine?<br/>
With the help of bastion server.


**Let's create EC2 machine and keep its name Bastion**

1. Go to EC2

2. Give the name of instance.

3. Select Linux OS.

4. Select keypair.

5. In the Network Settings. Click on Edit.

6. Select our own VPC

7. Select Public Subnet.

8. Auto Assign will be enable for our Public Subnet.

9. Create Security Group and give ssh port and MY IP means I can only connect to this particular machine. System will automatically will take your IP address.

10. With the help of this machine we will connect our private subnet machine.

11. Launch Instance

12. Now note down the private Ip of bastion server because we want to give private connection from bastion server to private subnet .

13. Connect Bastion server EC2 instances and from there connect bastion server to private EC2 instances.<br/>
    Switch User - sudo -i <br/>

    Update repository - yum update -y <br/>

    Copy SSH Command of database server & paste in putty<br/>

    Connect private subnet and click on connect and click on SSH client,copy SSH client and paste it in Bastion Server.Click on connect.<br/>

    You will get "permission denied"<br/>

    In this case we need PEM file instead of .ppk file. Means you need to transfer PEM file to Bastion Server using Winscp or any file transfer application.<br/>

    Open Winscp and copy public IP of bastion server.Connect to baston server and transfer PEM file.<br/>

    Run the same scp command and this time you will be able to connect to database server. Privately we are connected not publically.<br/>

    Switch User in private subnet- sudo -i <br/>

    Command to install MYSQL database - yum install mysql -y<br/>

    When you try to install database it will not install it get stuck after one line. Reason is we don't have internet access.
    
    To connect to internet we need public access and also internet connectivity. But in case of private subnet we don't need public access but we need to provide internet connectivity. 

    But can we provide public internet to private subnet? NO.

    **How we can provide internet access to private subnet?**

    We need to take help of NAT(Network Address Translation) gateway.


## NETWORK ADDRESS TRANSLATION

Network Address Translation help us to provide private internet access to private subnet.

A NAT (Network Address Translation) gateway is a managed AWS service that allows resources within a private subnet in an Amazon Virtual Private Cloud (VPC) to access the internet or other AWS services while preventing inbound traffic initiated from the internet from reaching those private resources.

NAT gateway is chargable because we need Elastic IP and creation of elastic IP is chargable that is why NAT gateway is chargable.

NAT gateway always creates in public subnet then link it with the help of route table in private subnet.


**Let's create NAT gateway**

1. Go to VPC.

2. Click on NAT gateway.

3. Click on create NAT gateway.

4. Give the name of NAT gateway

5. Select public subnet.

6. click on Allocate Elastic IP.

7. After creation link to subnet.

8. To link subnet go to route table.

9. Create route table.

10. Select own VPC.

11. create route table.

12. Select route table click on Action and edit subnet association.

13. Attach private subnet.

14. Now link routes. For that click on Action, edit route .

15. Select NAT Gateway. 

16. Give 0.0.0.0 as destination because we are providing internet connectivity.

17. Save changes.

18. Now try to install "yum install mysql -y". This time you will find it is installing.

**Now EC2 machine has private internet**


## NETWORK ACCESS CONTROL LIST

It is a security layer for our VPC that controls the traffic in and out of one or more subnets. It is an optional layer for our VPC.

It acts as a stateless firewall for controlling inbound and outbound traffic at the subnet level.

**Note**-Earlier also we are using security at that time we are using security group.<br/>
Security Group provide security at EC2 level and NACL provide seccurity at Subnet level.

Our custom VPC automatically comes with the default Network ACL which includes all inbound and outbound ipv4 traffic.

We can also create a custom network ACL and associates with a subnet. By default, a custom Network ACL denies all the inbound and outbound ipv4 traffic until you add rules.

Network ACL is associated with both inbound and outbound rules that can either deny or allow the rules.

NACLs evaluate rules in a sequential order, starting from the lowest-numbered rule to the highest. Each rule has a rule number, and the NACL processes the rules in ascending order.


**Let's create NACL**

1. Go to VPC.

2. Go to NACL.

3. You can see by default we are getting 2 NACL<br/>
   one with default VPC<br/>
   second one with our own VPC

4. Open default NACL. In default NACL by default everything is allow.

5. But you don't want to allow everything. You want to restrict rules.

6. Click on create NACL

7. Select own VPC.

8. create NACL.

9. To link NACL click on Action.

10. Edit subnet association.

11. Attach public subnet.

12. Save changes.

13. Open the web server in browser of public subnet. It will not open because we have created our own NACL and by default everything is deny for custom NACL.

14. Now we need to add our rules.

15. Click on Action.

16. Edit inbound rules.

17. Click on add rule number.

18. Give 100 to rule number.

19. Type - SSH

20. Give my Ip means under this subnet whatever the EC2 machines are there so only with help of my ip we can connect.

21. Save changes.

22. Edit outbound rules.

23. Click on add rule number.

24. Give 100 to rule number.

25. Type - SSH

26. Give my Ip means under this subnet whatever the EC2 machines are there so only with help of my ip we can connect.

27. Save changes.

28. Can we Now connect to webserver now? No. <br/>
    We have just added SSH rules. We need HTTPS access.

29. Enable HTTP to the inbound and outbound.

30. Click on inbound rules and add rule number.

31. Give 200 to rule number.

32. Type - HTTP

33. Give Public IP because we need internet access.

34. Save changes.

35. Click on outbound rules and add rule number.

36. Give 200 to rule number.

37. Type - HTTP

33. Give Public IP because we need internet access.

34. Save changes.

35. Try to access Webserver now.<br/>
    Again you are not able to access webserver.<br/>
    Reason is Ephemeral Ports


**NACL - Ephemeral Ports**

An ephemeral port is a temporary communication hub used for Internet Protocol (IP) communications.

Total Number of Ports are 0 to 65535 in networking but NAT gateway uses ports 1024-65535.

**For Example**: Assume in public subnet, we have 100 webservers. All are connected to load balancer. If hacker blocks any http port on 1 webserver. There is will be no problem for us because all other 99 webservers are working fine. As load balancer will send the request to other servers.

• But if hacker blocks any http port on NACL level (Subnet level). Entire website is down.

• To avoid this problem, AWS is providing range of ports (1024 - 65535). We need to open this range in NACL level, so when hacker blocks a particular port (HTTP), AWS uses a random port from the range. AWS will replace the random as HTTP port. So that website will never go down.

**Note**: Ephemeral ports are mandatory at NACL level

**Let's Enable Ephemeral rules**

1. Click on inbound rules and add rule number.

2. Give 300 to rule number.

3. Type - Custom TCP

4. Enter Port range (1024-65535)

5. Give 0.0.0.0 as source.

6. Save changes.

7. lick on outbound rules and add rule number.

8. Give 300 to rule number.

9. Type - Custom TCP

10. Enter Port range (1024-65535)

11. Give 0.0.0.0 as source.

12. Save changes.

13. Now let's try to access Webserver.<br/>
    This time you will be access your web server.

**Note**- You can also deny rules by giving particular IP but remember lower the number has highest priorty means you have to give lower rule number then only it will work.


## DIFFERENCE BETWEEN SECURITY GROUP AND NACL

**Security Group**

1. Operates at the Instance Level<br/>
2. It is first Layer of Defense <br/>
3. Support Allow rules Only<br/>
4. State-full: return traffic is automatically allowed, regardless of any rules<br/>
5. All Rules are evaluated before deciding whether to allow traffic<br/>
6. Security Group is applied to an instance only when you specify a security group while launching an instance.<br/>


**Network Access Control List**

1. Operates at Subnet Level.<br/>
2. It is Second Layer of Defense <br/>
3. Support Allow rules and Deny Rules <br/>
4. Stateless: return traffic must be explicitly allowed by rules (think of ephemeral ports)<br/>
5. Rules are evaluated in order (Lowest to highest) when decided whether to allow traffic , first match wins<br/>
6. NACL has applied automatically applies to all instances in the subnet it is associated with.<br/>







    


    
















































