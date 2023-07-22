## VIRTUAL PRIVATE CLOUD

Till the time whatever EC2 created we created in default VPC. A default VPC (Virtual Private Cloud) is a pre-configured VPC that is automatically created in each AWS region when you sign up for an AWS account. 

Default VPC is designed to provide a default networking environment for new AWS users, making it easier for them to launch resources and start using AWS services without the need for additional configuration.

But it is often recommended to create custom VPCs with specific network configurations tailored to your application requirements.

Custom VPCs offer more control over security, network architecture, and resource isolation, making them suitable for production environments and multi-tiered applications.

Custom VPC in AWS offers a private, secure, and customizable networking environment, providing the foundation for building and deploying applications with enhanced security, scalability, and connectivity. 

It is logically isolated from other virtual networks in the AWS Cloud. You can launch your AWS resources, such as Amazon EC2 instances, into your VPC.

A Custom virtual private cloud (VPC) is a virtual network dedicated to your AWS account.

**VPC is like under my AWS region I have taken my private space and I have complete control over that private space so that private space will be my VPC.**



**Key Features of AWS VPC**

1. VPC allows the user to select IP address range, create subnets, and configure route tables, network gateways, and security settings.

2. VPC allows VPC Peering connections with other VPC within the same or different AWS accounts.

3. It provides a feature of security such that the data stored in Amazon S3 can only be accessed from within your Amazon VPC.

4. We can resize the VPC.

5. Max VPC is 5 Per Region. We can increase this limit so that you can have 100s of VPCs per Region.

6. We can create 200 Subnets in one VPC & 1000 Subnets in one region


**VPC - Sizing**

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


**SUBNET**

In a Virtual Private Cloud (VPC) in Amazon Web Services (AWS), a subnet is a segmented portion of the VPC's IP address range. It is a way to partition the VPC into smaller, more manageable network segments.

Each subnet is associated with a specific CIDR (Classless Inter-Domain Routing) block, which is a range of IP addresses. Subnets within a VPC can be of different sizes and are used to isolate and organize resources within the VPC. Subnets play a crucial role in enabling the isolation and control of network traffic between different groups of resources.

**Earlier we were dividing aws region into parts called VPC**<br/>
**Now I am dividing the VPC into small-small parts called subnets**

**Subnets can be categorized into two main types:**

**Public Subnet**: A public subnet is a subnet that has a route to the internet through an Internet Gateway (IGW). Resources placed in a public subnet can have public IP addresses and are accessible directly from the internet. Common examples of resources placed in a public subnet are web servers, load balancers, and Bastion hosts.

**Private Subnet**: A private subnet is a subnet that does not have a direct route to the internet. Resources placed in a private subnet cannot be accessed directly from the internet. They can only communicate with the internet through a Network Address Translation (NAT) Gateway, a NAT instance, or through a VPC peering connection to a public subnet. Private subnets are often used to host backend servers, databases, and other internal resources that do not require direct internet access.


**By default when we create subnet under VPC it will be created as private subnet**

**For Subnet I need to give IP address range**

**Can we give any IP to subnet?**<br/>
No, the ip address range which we have given to VPC so In that range only we need to give to subnet.<br/>

I need to give Ip address in this 10.0.0.0/16 range <br/>

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

**While craeting subnets did we mentioned anything that define public subnet or private subnet?**
**By deafault all subnet are private subnets**

**Subnet - Make Subnet as Public**

1. Select public subnet.

2. Go to action

3. Click on edit Subnet setting.

4. click on enable auto assign public IPv4 address.














