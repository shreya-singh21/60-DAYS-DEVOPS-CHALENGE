
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
