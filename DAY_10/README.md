## Reachability Analyzer

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


**Benefits of VPC Peering**

• Improve Security

• Save Money On Network Costs

• Get more flexibility for services that don’t need to connect to the Internet.

**Limitations**

• We cannot perform peering if both VPC have same CIDR, but we can perform VPC if you have a different CIDR.

• We cannot edit the VPC peering connection once it is created.

• We cannot attach or detach VPC peering connection

• Once we accepted VPC peering request we can’t change or deny it later


**Let's create VPC Perring**

1. Create First VPC

2. Name the VPC - VPC1

3. Give the CIDR - 10.0.0.0/16

4. Create VPC

5. Craete Internet Gateway

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

11. create private subnet.

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

66. 









    











