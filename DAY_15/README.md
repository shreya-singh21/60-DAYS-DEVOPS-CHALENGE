
## AWS BACKUP

AWS Backup enables us to centralize and automate data protection across AWS services. AWS Backup offers a cost-effective, fully managed, policy-based service that further simplifies data protection at scale.

Let's imagine you have a bunch of important files and data stored in your computer. To make sure you don't lose anything, you might regularly create copies of those files on an external hard drive. AWS Backup works in a similar way, but for the cloud!

AWS Backup is like a super organized digital backup system for all your important stuff in Amazon Web Services (AWS). It helps you create backup copies of your data stored in various AWS services, like databases, file storage, and more.


**Here's how it works**:

**Backup Plan**: Think of this as your backup strategy. You tell AWS Backup how often you want to create backups and how long you want to keep them.

**Backup Vault**: This is like a super secure storage space where your backups are stored. A backup vault is a container that stores and organizes our backups. It's super reliable and you don't need to worry about managing it.

**Backup Copy**: AWS Backup takes a snapshot of your data at the scheduled times you've set. This snapshot is like a snapshot of your computer screen but for your cloud data.

**Restore**: If you ever lose your data or need to go back to a previous version, you can restore your data from the backup copy in the vault.


**Let's create EC2 backup** 

1. Create one EC2 machine.

2. Choose AWS linux machine, enter key pair, select t2.micro as intance type, create linux security group and launch instance.

3. Now go to aws backup

4. Click on create backup plan

5. Now we have three options to craete backup plan<br/>
   
   • Start with a template<br/>
   • Build a new plan <br/>
   • Define a plan using JSON<br/>

6. Select start with a template

7. There we will find four templates.Other than this we can create our own templete. But this time let's select Daily-35day-Retension.

8. Enter Backup plan name

9. Go to backup rules. We will find the default backup rules. Edit the backup rules.

10. Click on edit

11. Click on create new Backup Vault.

12. Enter Backup Vault name

13. Select default aws backup as Encryption Key

14. Now click on create Backup Vault.

15. Now select the backup frequency in backup rules configuration. Backup frequency is like daily, weekly, monthly you want to take backup.

16. Select Daily backup frequency

17. Now specify the backup timing.

18. Below we will find the Copy to destination section. In this we have to select destination region in which particular region we want to take backup. We can choose any region like singapore.

19. Click on save backup rules.

20. Click on create backup.

21. After creation of plan we have to assign EC2 resource.

22. Click on Assign Resources

23. Enter the resource assignment name

24. Select our resource<br/>

    • Include all resource type<br/>
    • Include specific resource type<br/>

25. Select the include specific resource types

26. Select specific resources types as EC2

27. Select Instance ID

28. Click on Assign resources

29. Now we have created the backup for our EC2 instance and this backup will trigger on daily basis.


## AWS DATASYNC

AWS DataSync is an online data transfer service that simplifies, automates, and accelerates the process of copying large amounts of data to and from AWS storage services over the Internet or AWS Direct Connect. It is like Backup.

Imagine you have two houses, and you want to keep them both furnished the same way. But carrying all the furniture between the two houses would be a lot of work. That's where a magical moving service like AWS DataSync comes in!

AWS DataSync helps you move data between different places, like from your on-premises servers to the cloud or between different cloud storage services. It's like a super efficient moving truck for your digital stuff.

So, whether you're moving data to the cloud, between different cloud services, or even back to your own servers, AWS DataSync is like your trusty moving service that takes care of all the heavy lifting. It's like having a team of digital movers that ensure your data gets to where it needs to be, hassle-free! 

**EFS to EFS**<br/>
We can do this datasync on same region and on cross region.


**DATASYNC IN SAME REGION**

1. To do this same region there is pre-requisite that we need one security group with port number 2049

2. Go to EC2.

3. Go to security group

4. Click on create security group 

5. Give the security group name

6. Add inbound rule.

7. Enter custom TCP with 2049 port and source will be anywhere

8. Click on create security group.

9. Now let's create EFS.

10. Go to EFS

11. Give the name of EFS

12. Click on customize

13. In security group, remove the default security group and add the security group which you have created

14. Click on next

15. Create EFS.

16. Now create one EC2 machine.

17. Go to EC2

18. Give the name of EC2.

19. Create key pair.

20. Create security group

21. Launch Instance.

22. Now with this EC2 machine I need to attach my security group with NFS port 2049.

23. Go to EC2 machine, click on Action, click on security group, add security group, clock on create.

24. Connect to EC2 machine.

25. Login with ec2-user

26. Now Switch user <br/>
    sudo su -

27. Install EFS Utils<br/>
    sudo yum install -y amazon-efs-utils

28. Create efs directory
    mkdir efs

29. Now we have to attach efs.

30. Go to our Elastic File system in GUI

31. Click on Attach

32. Copy our NFS Client Command and Paste in Putty

33. Now under efs we will create fil1, file2, file3.

34. Switch to efs folder<br/>
    cd efs

35. Create files<br/>
    touch file1 file2 file3

36. Now create second EFS from GUI

37. Go to EFS

38. Click on Create file system

39. Give the name of second efs

40. Click on customize

41. Click on Next

42. Remove default security group and change it with your security which you have created with NFS Port.

43. Click on create

44. After creating EFS, create second EC2 machine with different availability zone.

45. Go to EC2, give the name of EC2.

46. Enter the key pair

47. Give the security group of NFS port, SSH and HTTP

48. Launch the Instance

49. Now connect to second EC2 machine using putty.

50. Login as ec2-user

51. Switch user<br/>
    sudo su -

52. Install EFS Utils<br/>
    sudo yum install -y amazon-efs-utils

53. Create efs directory<br/>
    mkdir efs

54. Go to EFS in GUI

55. Click on Attach

56. Now copy the NFS Client & paste in putty

57. Now we have to create files in efs directory

58. Switch to efs directory<br/>
    cd efs

59. Create files<br/>
    touch file4 file5

60. In first efs we have file1, file2, file3 and second efs we have file4, file5.

61. Now go to aws datasync

62. In datasync you will get option<br/>
    Between on premise storage and AWS<br/>
    Between AWS Storage service

63. Select between aws storage service option

64. Select create a new location. In this we have to give the source details.

65. Select the service as source . Select Amazon EFS filesystem.

66. Select Region as Mumbai

67. Now select filesystem as EFS1.

68. Select subnet. 

69. Select the security group which you have attached with our EC2 machine. We have attached the NFS port security group and SSH.

70. 
   



    

