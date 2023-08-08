
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
   