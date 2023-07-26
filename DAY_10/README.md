## REACHABILITY ANALYZER

VPC Reachability Analyzer is a configuration analysis tool that enables us to perform connectivity testing between a source resource and a destination resource in our virtual private clouds (VPCs). At times, when customers are deploying large workloads in AWS, it is also quite difficult and time consuming to troubleshoot network connectivity issues mainly due to misconfigurations. This is where VPC Reachability Analyzer can help.

1. Create VPC.

2. Give the VPC name.

3. Enter IPV4 CIDR
   ex- 10.0.0.0/16

4. Create VPC.

5. Create Subnet.

6. Click on subnets

7. Select your VPC 

8. Enter subnet name, Select availability zone & Enter 10.0.1.0/16 CIDR Block.

9. Click on Create subnet.

10. Click on edit Subnet setting.

11. click on enable auto assign public IPv4 address.

12. Go to internet gateway.

13. Give the name of internet gateway

14. create internet gateway

15. After creation of internet gateway will get popup saying that "Attach to a VPC". Click on that popup.

16. Create route table.

17. Click on route table

18. Give the name of route table

19. Select your VPC

20. Click on create route table.

21. Edit Subnet Association

22. Edit routes

23. Click on add routes

24. Select Internet Gateway as target

25. Give 0.0.0.0 as destination. 0.0.0.0 means open to all.

26. Create Linux EC2 Machine in our VPC & Subnet

27. Enable SSH Port 

28. Go to VPC

29. Click on Reachability Analyzer 

30. Click on create and analyze path

31. Enter the name

32. Select sourec and destination means from which source and destination you want to check connectivity.

33. Select the Source type (Instances)

34. Select the source as EC2

35. Select the Destination type (Internet Gateway)

36. Select the destination as Internet gateway ID

37. Click on create and analyze path

38. Now in Reachability Analyzer you will see the whole path

39. Now if you disconnect the connectivity means if you remove the internet gateway from route table 

40. Check the Reachability Analyzer. Go to Action and view details you will find one more time it will run and it shows error. You can check where error is showing and you can rectify it.


## VPC - PEERING

A VPC peering connection is a networking connection between two VPCs that enables routing of traffic between them using private IP addresses. VPC peering connection can be established between our own VPCs, or with a VPC in another AWS account in a single different region.

**In simple words** : Connectivity between two or multiple VPCs called as VPC Peering.

In this we will create 2 VPCs: VPC1 and VPC2.<br/>
In VPC1 we will create 2subnets : public subnet and private subnet.<br/>
In VPC2 we will create 1 subnet : private subnet<br/>
In VPC1 we will do peering between public subnet and private subnet<br/>
Finally we will do peering between two VPCs and will mention subnet in which we want to do peering like private subnet of VPC1 and private subnet of VPC2.<br/>
Also we enable SSH port on both machine beacuse it is mandatory if we want to do connection between 2 machines.


**BENEFITS**

• Improve Security

• Save Money On Network Costs

• Get more flexibility for services that don’t need to connect to the Internet.

**LIMITATION**

• We cannot perform peering if both VPC have same CIDR, but we can perform VPC if you have a different CIDR.

• We cannot edit the VPC peering connection once it is created.

• We cannot attach or detach VPC peering connection

• Once we accepted VPC peering request we can’t change or deny it later


**Let's create VPC Perring**

1. Create First VPC

2. Name the VPC - VPC1

3. Give the CIDR - 10.0.0.0/16

4. Create VPC

5. Create Internet Gateway

6. Attach to VPC1

7. Create 2 Subnets

8. Select VPC1

9. Give name of subnet - Public-subnet-1

10. Give CIDR to public subnet - 10.0.1.0/16

11. Click on subnet. Click on Edit.

12. Click on auto assign public ip

13. Create 2nd subnet in VPC1

14. Give name of subnet - Private-subnet-1

10. Give CIDR to private subnet - 10.0.2.0/16

11. Create private subnet.

12. Create Route table

13. Give the name of route table. Attach VPC. Create it

14. Click on Action.

15. Edit subnet association

16. Assign public subnet.

17. Edit routes

18. Select target as Internet Gateway and destination as 0.0.0.0/0

19. Create EC2 machines

20. Create Linux EC2 Machines in Public Subnet

21. Create Security Group

22. Select type as SSH & Source as My IP

23. Click on Launch Instances

24. Create another EC2 in VPC1

25. Create Linux EC2 Machines in Private Subnet

26. Create Security Group

27. Select type as SSH & source as custom and give 10.0.1.0/16 means we are giving access to complete subnet so that whatever the EC2 machine are there in public subnet all can access to private subnet.

28. Launch the Instance

29. We have done setup for our first VPC

30. Create Second VPC

31. Name the VPC - VPC2

32. Give the CIDR - 28.200.0.0/16

33. Create VPC

34. Create subnet.

35. Give name of subnet - Private-subnet-2

36. Give CIDR to public subnet - 28.200.1.0/16

37. Create subnet.

**Note**- In second VPC we will not create internet gateway and route table because we don't need internet connection here.

38. Create EC2 machines

39. Create Linux EC2 Machines in Private Subnet

40. Create Security Group

41. Select type as SSH & source as custom and give 10.0.2.0/16 means we are giving access to complete subnet so that whatever the EC2 machine are there in private subnet VPC1 all can access to private subnet VPC2.

42. Also enable ping request to check connection between 2 VPCs<br/>
    Enable ICMP IPV4 and give 10.0.2.0/16 IP.

43. We have done setup for our second VPC

44. Connect Public-Subnet-1 of VPC1.

45. Now connect to Public-Subnet-1 of VPC1 to Private-Subnet-1 of VPC1<br/>
    To connect from public to private copy ssh command from Private EC2 instance and paste it in putty of public EC2 insatnce<br/>
    Previously we have seen that you will get an error because we need a PEM file.<br/>
    Earlier we were transfering PEM fuile with the help of winscp but we can also create it with the help of linux command.<br/>
    Everytime we cannot go with winscp because if we have to connect public intsnace to private instance we can go with winscp but if we have to connect private instance to another private instance this time we cannot go with winscp because there we need to provide public IP and we do not have public ip so we can go with linux commna dof creating PEM file.

46. Create pem file in the instance of Our Private Instance from first VPC - vim <pemfilename>.pem

47. In this PEM file we need to give some code. Open pem file in Notepad++

48. Copy the complete code & paste the code in putty

49. Change the permission of the file - chmod 400 <pemfilename>.pem

50. Switch user - sudo su

51. Connect Private Instance from first VPC<br/>
    paste SSH command of Private Instance

52. Now you will able to connect.

53. Now we need to connect from Private EC2 instance of VPC1 to Private EC2 instance of VPC2

**Note** - Here if we try to connect Private EC2 instance of VPC1 to Private EC2 instance of VPC2 with the help of PEM file then this will not work because here we don't have connection between VPC1 and VPC2.

54. We need to make the connectivity between two VPCs.

55. Create Peering Connections

56. Select Peering Connections

57. Click on Create Peering Connections

58. Enter the name

59. Select the Requester (First VPC)

60. Select my Account

61. same region

62. Select the Accepter (Second VPC)

63. Click on Create Peering Connections

64. This peering connection will not going to automatically setup. We need to accept the peering request.

65. Check if you able to connect Private EC2 instance of VPC2 with SSH command. <br/>
    No

66. We need to link the subnets means we need to craete routes in our both the subnets.

67. Create route table for first VPC

68. Go to route table. Create route table.

69. Give the name of route table.

70. Attach VPC1

71. Create route.

72. Click on Action. Edit subnet association.

73. Select private subnet.

74. Click on Action. Edit routes

75. Earlier we used to select "internet gateway" now this time we will select "peering connection". Give 28.200.0.0/16 IP address as destination because this time we are linking subnets with each other. We want to private subnet of VPC1 to private subnet of VPC2 so that is why in VPC1 we gave the ip of private subnet VPC2.

76. Same thing we have to do in VPC2

77. Create route of VPC2.

78. Click on Action. Edit subnet association.

79. Select private subnet.

80. Click on Action. Edit routes.

81. Give target as peering connection and destination as 10.0.2.0/16 (private subnet of VPC1)

82. Try to connect machine from private subnet of VPC1 to private subnet of VPC2 with the help of ssh command of private subnet of VPC2.

83. This time we will able to connect.

84. Also we can do ping request from private subnet of VPC1 to private subnet of VPC2 - ping 28.200.0.0/16, it will work.

85. **Can we do ping request from private subnet of VPC2 to private subnet of VPC1?**<br/>
      No, because in the private subnet of VPC2 we haven't enable ping request.<br/>

86. Go to Security group and enable ping request.<br/>
    Enable ICMP IPV4 and give 28.200.0.0/16 IP.

87. Now the ping request will work from VPC2 of private subnet.


## VPC - ENDPOINT

A VPC endpoint enables us to privately connect our VPC to support AWS services. Instances in our VPC do not require Public IP Addresses to communicate with resources in the service. They remove the need of Internet Gateway, Nat Gateway and VPN Connection to access AWS services.

**ENDPOINTS - TYPES**

• Interface Endpoint

• Gateway Endpoint

**INTERFACE ENDPOINTS**:

Interface Endpoints are powered by AWS PrivateLink and provide private access to AWS services that are integrated with PrivateLink. These services have their own service-specific endpoint names, and they use Elastic Network Interfaces (ENIs) to establish connections between your VPC and the AWS service.

Interface Endpoints use private IP addresses, and the traffic stays within the AWS network, ensuring a secure and efficient communication channel.

Some AWS services that support Interface Endpoints through AWS PrivateLink include Amazon S3, Amazon DynamoDB, Amazon API Gateway, Amazon CloudWatch, and more.

**GATEWAY ENDPOINTS**:

Gateway Endpoints are used for accessing AWS services that support VPC endpoints but are not integrated with AWS PrivateLink. These endpoints use VPC route tables to route traffic directly to the service, making them easy to set up and manage.

Gateway Endpoints do not require ENIs, and they are associated with specific route tables in your VPC to direct traffic to the appropriate service.

As of now, Amazon S3 and Amazon DynamoDB support Gateway Endpoints for VPC access.

In this we will create 1 VPC<br/>
Under VPC we will create public subnet and private subnet
Then we will connect s3 bucket with private subnet with the help of VPC Endpoint.


**Let's create VPC Endpoint**

1. Create First VPC

2. Name the VPC - VPC

3. Give the CIDR - 10.0.0.0/16

4. Create VPC

5. Create 2 Subnets

6. Give name of subnet - Public-subnet-1

7. Give CIDR to public subnet - 10.0.1.0/16

8. Click on subnet. Click on Edit.

9. Click on auto assign public ip

10. Create 2nd subnet in VPC1

11. Give name of subnet - Private-subnet-1

12. Give CIDR to private subnet - 10.0.2.0/16

13. Create private subnet.

14. Create Internet Gateway

15. Attach to VPC

16. Create route table

17. Select VPC

18. Click on Action.

19. Edit subnet association

20. Assign public subnet.

21. Edit routes

22. Select target as Internet Gateway and destination as 0.0.0.0/0

23. In this we need two route tables. one we attach with public subnet and other we attach with private subnet.<br/>
    Also we have two route tables. One is just we created and earlier we have seen that whenever we creates VPC, AWS will create route table for use so that routw table will use.

24. Attach the default route table with private subnet. For public subnet we have already created route table and attached to    public subnet.

25. Now Create End point

26. Go to Endpoint

27. Click on Create endpoint

28. Find S3

29. Select VPC

30. Select Private Subnet route table beacuse we are linking aws service with private subnet and then private subnet to public subnet.

31. Create Endpoint.

32. Create EC2 machines

33. Create Linux EC2 Machines in Public Subnet

34. Create Security Group

35. Select type as SSH & Source as Anywhere

36. Launch Instance.

37. Create another EC2 machines

33. Create Linux EC2 Machines in Private Subnet

34. Create Security Group

35. Select type as SSH & Source as 10.0.1.0/16(public subnet instances can access private subnet instances)

36. Launch Instance.

37. Now we are going to connect public machine and from public machine will connect private machine.

38. Connect Public machine of VPC.

39. Create Pem file to connect Private instance using Public Instance - vim <pemfilename>.pem

40. Change the Permissions - chmod 400 <pemfilename>.pem

41. switch user - sudo su

42. Copy & Paste the SSH Command of Private Instance

43. We will be connected to private subnet.

44. Earlier when we are using S3 service we are working with public subnet in case of NAT gateway. Now this time we are using private subnet.

45. switch user - sudo su

46. Connect to aws. Command to connect aws. Configure AWS - aws configure

47. Now generate access key ID and secrate key ID

48. Give the access key and secrate key ID

49. Enter Region - ap-south-1

50. Enter format - text

51. Create S3 Bucket - aws s3 mb s3://<Bucket_Name>

52. List of S3 Buckets - aws s3 ls

**Note** - Right now what we have created s3 we can create it from local machine, public machine so what is the purpose of endpoint and create s3 .<br/>
          If we delete endpoint then we cannot create S3 and like in NAT gateway we don't need internet connection here.

**Endpoint is used whenever we want to connect aws service privately**    


## VPC - FLOW LOGS

VPC Flow Logs is a feature that enables you to capture information about the IP traffic going to and from network interfaces in your VPC. Flow log data can be published to Amazon CloudWatch Logs or Amazon S3.


1. Create VPC

2. Name the VPC - VPC

3. Give the CIDR - 10.0.0.0/16

4. Create VPC

5. Create Subnet

6. Give name of subnet - Public-subnet

7. Give CIDR to public subnet - 10.0.1.0/16

8. Click on subnet. Click on Edit.

9. Click on auto assign public ip

10. Create Internet Gateway

11. Attach to VPC

12. Create route table

13. Select VPC

14. Click on Action.

15. Edit subnet association

16. Assign public subnet.

17. Edit routes

18. Select target as Internet Gateway and destination as 0.0.0.0/0

19. Create EC2 machines

20. Create Linux EC2 Machines in Public Subnet

21. Create Security Group

22. Select type as SSH & HTTP port and Source as Anywhere

23. Give the bootstarp script<br/>
    #!/bin/bash<br/>
    sudo su<br/>
    yum update<br/>
    yum install httpd<br/>
    cd /var/www/html<br/>
    echo "AmazonWebservices" > index.html<br/>
    service httpd start<br/>
    chkconfig httpd on<br/>

24. Launch Instance.

25. Check the public Ip of EC2 machine in the browser<br/>
    It will open.


**FLOW LOGS – S3**

1. Create S3 Bucket & Don’t give public Access

2. Go to S3.

3. create bucket

4. Giv ethe name of bucket.

5. Click on create bucket.

6. Now create flow logs in S3.

7. Go to VPC service. Select your VPC.

8. Below down we will find Flow logs section.

9. Create flow logs

10. Give the name of flow logs

11. Select filter <br/>
    Accept <br/>
    Reject <br/>
    All <br/>

12. Maximum Aggregation interval<br/>
    10 minutes<br/>
    1 minutes<br/>

13. Destination<br/>
    Send to an Amazon S3 Bucket

14. Give s3 bucket ARN<br/>
    To get s3 bucket ARN. Go to s3, select bucket you will get ARN. Copy ARN.

15. Select Log record format<br/>
    AWS default format<br/>
    Custom format

16. Click on create flow logs

17. Now go to s3, under bucket you will get logs


**FLOW LOGS – CLOUD WATCH**

1. Go to cloudwatch service

2. Go to log grups. Under this log group aws is creating logs

3. Give the name of log group

4. Select Retention days (After how many day aws log get expired)<br/>
   Select never expire

5. Create log group.

6. Now go to VPC

7. Click on flow logs

8. Click on create flow logs

9. Give the name of flow logs

10. Select filter as All

11. Select Maximum aggregation interval & Select Cloud Watch Logs

12. Give the destination log group which we have created in the starting of cloudwatch logs

13. To create this log group we need IAM role.<br/>
    Create IAM role<br/>
    Create policy<br/>
    select cloudwatch service<br/>
    Select actions <br/>
    In list Select (DescribeLogGroups, DescribeLogStreams)<br/>
    In Write Select (CreateLogGroup, CreateLogStream, PutLogEvents)<br/>
    Select resource as all resources<br/>
    Give policy name<br/>
    create policy<br/>

    Now create role<br/>
    Select custom trust policy<br/>
    We need to give seprate json code<br/>
    {<br/>
    "Version": "2012-10-17",<br/>
    "Statement": [<br/>
        {<br/>
            "Sid": "",<br/>
            "Effect": "Allow",<br/>
            "Principal": {<br/>
                "Service": "vpc-flow-logs.amazonaws.com"<br/>
            },<br/>
            "Action": "sts:AssumeRole"<br/>
        }<br/>
    ]<br/>
}<br/>
    Click on Next<br/>
    Select the policy which we have created<br/>
    Enter the role name & description<br/>
    Click on create role<br/>

14. Go back to VPC. select IAM role

15. Click on create Flow logs

16. Go to cloudwatch log group

17. Click on search log group

18. There we will find the logs


**Note**- In real time it is difficult to read those logs because there are 100s of lines logs.

To resolve ths issue we have Athena service. Wth the help of this we can read logs very easily by running few sql queries.It is showing in table format.We can link s3 bucket with this Athena service.


## S3 - ATHENA

Amazon Athena is a server less query service that makes analysis of data, using standard SQL, stored in Amazon S3 simpler. With few clicks in the AWS Management Console, customers can point Amazon Athena at their data stored in Amazon S3 and run queries using standard SQL to get results in seconds.

In Athena service we have to link s3 bucket.

1. Click on Edit Settings.

2. Browse our s3 bucket

3. Select the existing s3 bucket where we are storing VPC Flow Logs

4. Click on choose & Save

5. Go to Editor and start creating our tables.

6. So under particular dates whatever files we have sytem will going to read it.


## AWS - VPN CONFIGURATION (OPENVPN)

Amazon Web Services (AWS) offers Virtual Private Network (VPN) solutions to securely connect your on-premises network or data center to your AWS VPC (Virtual Private Cloud) over the internet. A VPN establishes an encrypted tunnel between your local network and the AWS cloud, enabling secure communication and data transfer between the two environments.

1. Check our Public IP<br/>
   Go to browser and type whatismyipaddress. We will get our Ip address

2. Create Open VPN EC2 Machine

3. Go to EC2 machine

4. Give name

5. There are predefine AMI we have in AWS<br/>
   click on Browse more AMI

6. We have AWS marketplace AMI. This is the third party AMI

7. Search OpenVPN

8. Click on select

9. Click on Continue

10. Select the Instance type as t2.micro

11. Use Default VPC & Subnet

12. System is creating the Security group.

13. Launch the instance

14. Note down EC2 machine public IP

15. Connect EC2 Machine with Putty

16. Earlier we are using username as ec2-user for linux type of instances but this time we are using openVPN and openVPN is of Ubuntu type of operating system.

17. So default username will be root.

18. It will install openVPN using root user.

19. Now it will ask you to login vpn

20. Again connect putty with user openvpnas

21. Now set openVPN password

22. Command to set password - sudo passwd openvpn

23. Enter our Password

24. Now try to connect your private network<br/>
    https://<publicip>:943/admin

25. Enter username (openvpn) & password

26. Click on sign in

27. Click on Agree

28. In openVPN we will enable one option

29. Click on VPN Settings

30. Go to Routing

31. Select yes for Internet traffic

32. Click on save setting

33. Now Login with user access<br/>
    https://<publicip>:943/

34. Enter our username (openvpn) & password

35. Download openvpn as per the operating system

36. Click on more info & then Click on Run anyway

37. Accept the terms & Install

38. Open tool openvpn

39. Click on Connect

40. Enter username & password

41. Check the IP Address from whatismyipaddress.com. You will find your system is connected with OpenVPN a private network.
    Your system Ip address has changed to openvpn ip address.






   






















    











