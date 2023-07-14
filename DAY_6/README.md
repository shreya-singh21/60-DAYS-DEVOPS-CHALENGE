# DAY 6 OF DEVOPS LEARNING
Building upon our previous knowledge gained during the first five days of our 60 Days DevOps Challenge, where we explored cloud computing, the benefits of Linux in DevOps, concepts related to EC2 instances, and the fundamentals of Amazon EBS and EFS, we are now ready to delve deeper into AWS storage services. In Day 6, we will focus on important topics such as Snapshots, Amazon Machine Images (AMIs), Scheduled Snapshots, Data Lifecycle Manager, and the Recycle Bin. These storage features will enhance our data protection, backup management, automation capabilities, and overall efficiency in managing our AWS infrastructure. Let's continue our journey of becoming proficient in DevOps practices and AWS services.

# AWS Storage Services Overview

In today's digital world, data storage is a critical aspect of any business or organization. Amazon Web Services (AWS) provides a wide range of storage solutions to meet diverse needs, from small-scale startups to large enterprises. This readme file provides a comprehensive overview of AWS storage services, including their types, features, advantages, and disadvantages.

## Amazon EBS (Elastic Block Store)

When you create an EC2 instance, it comes with a primary storage volume called the root volume. This volume contains the operating system and other essential files needed for the instance to function. The size of the root volume is determined when you launch the instance.

### Requirements for Additional Storage

As your needs grow, you might require more storage space for your data without affecting the root volume. In this case, you have two options:

1. Increase the size of the root volume: You can modify the instance settings to increase the storage capacity of the root volume. However, deleting this instance in the future will result in the permanent loss of all data on the root volume.

2. Create a separate EBS volume: Instead of increasing the size of the root volume, you can create a new EBS volume with the desired size. This volume can be attached to your EC2 instance as an additional drive, providing extra storage space for your data.

### Advantages of Using EBS Volumes

Here's where the advantage of using EBS volumes comes in:

1. Persistence: Unlike the root volume, which is tied to the lifecycle of the EC2 instance, the separate EBS volume remains independent. If you delete the EC2 instance, the data on the EBS volume is not lost. You can attach the EBS volume to another EC2 instance and access your data seamlessly.

2. Flexibility: By having a separate EBS volume, you can manage your data separately from the operating system and applications. It allows you to store important files, databases, or application data without the risk of accidental deletion during instance termination.

3. Scalability: With EBS volumes, you can easily increase or decrease the size of the volume as per your needs. If you require more storage space, you can modify the volume size without affecting the root volume.

### Use Case Example

For example, let's say you have an EC2 instance running a web server. The root volume contains the operating system and web server software. However, the user-uploaded files, such as images or documents, need additional storage. Instead of increasing the size of the root volume, you can create a separate EBS volume and mount it as a data drive. This way, you can scale the storage capacity independently without modifying the root volume.

In summary, while you can increase the size of the root volume, creating a separate EBS volume provides benefits such as data persistence, flexibility, and scalability. It allows you to manage your data separately and retain it even if the EC2 instance is deleted or replaced.

## Creating Elastic Block Storage on Linux

1. Create a Linux EC2 machine with the desired specifications.

2. During the EC2 instance creation process, add an additional EBS volume (e.g., 6GB) from the "Configure Storage" section. Optionally, check the "Delete on Termination" box if you want to delete the volume when terminating the instance.

3. Launch the instance.

4. Go to the "Volumes" section in the AWS Management Console and check the attached extra volume. You will see two volumes: the default root volume (e.g., 8GB) and the additional volume (e.g., 6GB).

5. Connect to the Linux EC2 machine using a SSH client, such as Putty or Terminal.

6. Use the Linux command `df -Th` to check the currently linked hard disks to the EC2 machine. Note that you won't find the additional 6GB volume because it has been attached but not mounted.

7. To check the attached volumes, use the command `lsblk`. Here, you will find both volumes.

8. To mount the volume, create a file system on it. Use the command `sudo mkfs -t ext4 /dev/xvdf` to create an ext4 file system on the volume.

9. Create a directory of your choice, e.g., `mkdir test`.

10. Attach the newly created directory to the volume using the command `sudo mount /dev/xvdf test`.

11. Change the current directory to the newly attached volume using the command `cd test`.

12. Now, you can create files in the test folder, e.g., `sudo touch file1 file2 file3`.

13. Run the `df -Th` command again to check the mount point. This time, you will see the additional volume with its path.

## Detaching and Attaching Volumes to Another EC2 Instance

To detach the volume from one EC2 instance and attach it to another without losing data, follow these steps:

14. First, detach the volume from the current EC2 instance by unmounting it with the command `sudo umount test`.

15. Run `df -Th` to verify that the volume is no longer mounted.

16. In the AWS Management Console, navigate to the "Volumes" section, select the 6GB volume, click on the "Actions" button, and choose "Detach Volume".

17. Create a new EC2 instance in the same availability zone as the detached volume.

18. During the instance creation process, ensure that the new instance is in the same availability zone as the detached volume.

19. Launch the new EC2 instance.

20. In the "Volumes" section, select the 6GB volume, click on the "Actions" button, and choose "Attach Volume".

21. Connect to the new EC2 instance using a SSH client.

22. Again, run the `df -Th` command to check the available volumes. You will not be able to see the 6GB additional volume until you mount it.

23. Note down the volume name from the `lsblk` command.

24. Create another directory, e.g., `mkdir training`.

25. Mount the volume to the new directory using the command `sudo mount /dev/xvdf training`.

26. Change the current directory to the newly attached volume using the command `cd training`.

27. List the files using `ls`. You will find all the files that were previously created in the test volume.

Now, you have successfully created and mounted an additional EBS volume on a Linux-based EC2 instance. You have also learned how to detach the volume from one instance and attach it to another without losing data.


## Let's create the Elastic Block Storage on Windows based Operating System

In this section, we will perform the same example that we did with a Linux-based OS. We will first add an additional volume to the EC2 machine, and then we will detach the existing volume and attach it to a new EC2 machine.

1. Go to the EC2 console and create a Windows-based EC2 machine.

2. Add a 5GB extra volume from the "Configure Instance" storage section and launch the instance.

3. Now create a second machine without an additional volume.

4. Connect to the first Windows machine using a remote desktop connection.

5. After connecting to the first Windows machine, go to "This PC." There, you will not be able to see the 5GB additional volume because the volume we just added is not mounted.

6. To mount the volume to the Windows EC2 machine, we need to use the "Server Manager" tool. Click on the Windows button and type "Server Manager" to open it.

7. In Server Manager, click on "File and Storage Services." This is where we will mount the volume.

8. Click on "Disks" in the left-hand pane. You will find your 5GB additional volume with an "Offline" status. We need to bring it "Online."

9. Select the 5GB volume, right-click on it, and choose "Bring Online."

10. Right-click on the volume again and click on "Initialize."

11. Once again, right-click on the volume and select "New Volume." A prompt will open where you need to specify the size of the volume, name of the drive, and create it.

12. Check "This PC," and you will find the additional 5GB volume listed.

13. Create a new Notepad file in the 5GB volume.

14. Now, let's mount the same volume to the second Windows EC2 machine. But before that, we need to unmount the volume from the first EC2 machine.

15. Go to "Server Manager," click on "Disks," click on the 5GB volume, and choose "Bring Offline." This will unmount the volume.

16. Next, we need to detach the volume. Go to the EC2 console, navigate to the "Volumes" section, select the volume, click on "Actions," and choose "Detach Volume."

17. Now, we can attach this existing volume to the second EC2 machine. Go to the "Volumes" section, click on "Actions," and select "Attach Volume" for the second EC2 machine.

18. Connect to the second EC2 machine using a remote desktop connection. Open "Server Manager." Select the 5GB volume, right-click on it, and choose "Bring Online."

19. Check "This PC" on the second EC2 machine, and you will see the additional volume with the same Notepad file and its contents.

**This is how we create an EBS volume and attach the same volume to another EC2 machine on a Windows-based Operating System.**


# Amazon EFS (Elastic File System)

When working with Amazon EC2 instances, there may be requirements for shared file storage that can be accessed across multiple instances. This is where Amazon EFS (Elastic File System) comes into play. Amazon EFS provides a scalable and fully managed file storage service that can be easily shared across multiple EC2 instances.

## Overview

While Amazon EBS (Elastic Block Store) provides storage for individual EC2 instances, Amazon EFS serves a different purpose. EFS is designed to provide shared file storage that can be accessed by multiple EC2 instances simultaneously.

Think of it this way: Amazon EBS is like having your own personal hard drive attached to your computer. You can store and access your files whenever you need. But what if you want to share those files with other people? You would need a shared network drive that can be accessed by multiple computers at the same time. This is where Amazon EFS comes in.

With Amazon EFS, you can create a shared file system that acts as a network drive for your EC2 instances. It allows multiple instances to access and share the same set of files, making collaboration easier. This is particularly useful in scenarios where you have multiple instances serving a web application, running data analytics, or managing content.

## Shared File Storage Requirements

When multiple EC2 instances need access to shared file storage, you have a few options:

1. Set up a centralized file server: You can create a standalone EC2 instance and configure it as a file server using technologies like NFS (Network File System) or Samba. This approach requires manual setup and maintenance of the file server instance.

2. Utilize Amazon EFS: Amazon EFS provides a fully managed, scalable, and shared file storage solution. With Amazon EFS, you can create a file system that can be mounted across multiple EC2 instances simultaneously, enabling easy file sharing and collaboration.

## Advantages of Using Amazon EFS

Here are some key advantages of utilizing Amazon EFS for shared file storage:

- Scalability: Amazon EFS automatically scales its storage capacity to accommodate growing data needs. As you add more files and data to the file system, Amazon EFS expands to handle the increased demand seamlessly.

- Elasticity: With Amazon EFS, you don't need to worry about pre-provisioning storage capacity. The file system automatically scales up and down based on your actual usage, ensuring that you have the right amount of storage at all times.

- Shared Access: Multiple EC2 instances within the same AWS region and security group can concurrently access and share the same file system. This allows for collaboration and coordination across instances, making it suitable for various use cases such as web hosting, content management systems, and data analytics.

- Durability and Availability: Amazon EFS is designed for high durability and availability. It stores data across multiple availability zones within a region, ensuring that your data remains accessible even if an availability zone experiences an outage.

## Use Case Example

Consider a scenario where you have multiple EC2 instances serving a web application that requires access to a shared set of static files, such as images, CSS, or JavaScript files. Instead of manually managing file synchronization across instances, you can create an Amazon EFS file system and mount it on each EC2 instance. This allows all instances to access the same set of files, ensuring consistency and simplifying the management of shared content.

## Let's Create Elastic File System

1. Go to the EFS (Elastic File System) console.

2. Provide a name for your EFS file system.

3. Select the standard storage class.

4. Click on the "Customize" button.

5. Choose "Bursting" under throughput mode and "General Purpose" under performance mode.

6. You can go with the default security group or create your own security group. For now, we will use the default security group.

7. Launch the first Linux EC2 machine.

8. Create a second Linux EC2 machine, making sure to select a different subnet from the first machine.

9. Select the existing security group (same as the first machine), or create a new security group if desired. In our case, we selected the default security group.

10. Connect to the first Linux machine and switch to the root user:
    `sudo su -`

11. Install EFS Utils:
    `sudo yum install -y amazon-efs-utils`

12. Create an EFS directory:
    `mkdir efs` (mandatory)

13. Link the EFS with the `efs` directory:
    - Go to the EFS console.
    - Click on the EFS file system.
    - Click on "Attach," copy the NFS Client command, and paste it into the Putty terminal. This will automatically attach the EFS file system to the `efs` directory.

14. Create some files in the `efs` directory:
    - Change directory to `efs`: `cd efs`
    - Create files: `touch file1 file2 file3`

15. Connect to the second Linux machine.

16. Switch to the root user:
    `sudo su -`

17. Install EFS Utils:
    `sudo yum install -y amazon-efs-utils`

18. Create an EFS directory:
    `mkdir efs` (mandatory)

19. Run the NFS command for the second machine.

20. Switch to the `efs` folder:
    `cd efs`

21. Run the `ls` command.
    - You will find the files created in the first Linux EC2 machine appearing in the second Linux machine.

22. If you create files in the second Linux machine, they will also appear in both EC2 machines.

**Note**: In Amazon EFS, you are creating files in a common shared location, and anyone can access them from anywhere.


# Snapshots

Snapshots in Amazon Web Services (AWS) refer to point-in-time copies of your block storage data, such as EBS volumes or root volumes. They serve as a secure data protection solution and offer several benefits for data backup, disaster recovery, migration, and compliance purposes. Snapshots are stored in Amazon S3.

## Key Points

- Data Protection: Snapshots provide a reliable way to protect your block storage data. They capture the exact state of your volumes at a specific moment in time, allowing you to restore data in case of accidental deletion, system failures, or other incidents.

- Disaster Recovery: Snapshots enable disaster recovery by providing a backup of your data. In the event of data loss or failure, you can create new volumes from snapshots to restore your applications and services quickly.

- Data Migration: Snapshots facilitate data migration across regions or AWS accounts. You can create a snapshot in one region or account and copy it to another, allowing you to replicate data and ensure availability in different locations.

- Backup Compliance: Snapshots can assist in meeting backup compliance requirements. By taking regular snapshots, you ensure the ability to recover and retain data for a specified period, complying with data protection regulations.

- Direct Attachment: Directly, you can't attach a snapshot to any instance. Snapshots serve as a source for creating new volumes rather than being directly attachable.

- Convert Snapshot to Volume: To utilize the data in a snapshot, you can convert it into a new EBS volume. This allows you to create a new volume with the same data as the snapshot and attach it to an EC2 instance.


## Creating Snapshots

To create a snapshot in AWS:

1. Launch an EC2 instance in your desired region.
2. Add an EBS volume to the instance if needed.
3. Navigate to the Elastic Block Store (EBS) service and locate the Volumes section.
4. Select the volume you want to create a snapshot for.
5. Choose "Create Snapshot" from the Actions menu.
6. Enter a name and optional tags for the snapshot.
7. Disable the reboot option.
8. Click on "Create Snapshot" to initiate the snapshot creation process.

## Using Snapshots to Create a Copy of an EC2 Machine

Snapshots allow you to create a copy of your EC2 machine and its data. Here's how you can do it:

1. Create a snapshot of the EBS volume attached to your EC2 machine using the steps mentioned above.
2. Once the snapshot is created, navigate to the Snapshots section in the Elastic Block Store (EBS) service.
3. Select the snapshot you want to use to create a new EC2 machine.
4. Choose "Create Volume" from the Actions menu.
5. Specify the desired volume size and other configurations.
6. Click on "Create Volume" to create a new EBS volume from the snapshot.
7. Launch a new EC2 instance and attach the newly created EBS volume.
8. The new EC2 instance will have an identical copy of the original EC2 machine, including all the data and configurations.

## Using Snapshots to Create EC2 Machines in Different Regions

Snapshots also enable you to create EC2 machines in different regions using the same data and configurations. Here's how you can do it:

1. Create a snapshot of the EBS volume attached to your EC2 machine using the steps mentioned above.
2. Once the snapshot is created, navigate to the Snapshots section in the Elastic Block Store (EBS) service.
3. Select the snapshot you want to use to create a new EC2 machine.
4. Choose "Copy" from the Actions menu.
5. Select the destination region where you want to create the new EC2 machine.
6. Click on "Copy" to copy the snapshot to the destination region.
7. Launch a new EC2 instance in the destination region using the copied snapshot.
8. The new EC2 instance will have the same data and configurations as the original EC2 machine but in the desired region.

In summary, snapshots provide a convenient way to create copies of EC2 machines and their associated data. You can use snapshots to create new EC2 machines with identical configurations, or even replicate machines in different regions. This flexibility and ease of use make snapshots a valuable tool for managing and scaling your AWS infrastructure.


# Schedule Snapshot (Event Bridge)

Scheduled Snapshots using Event Bridge is a feature in Amazon Web Services (AWS) that allows you to automate the creation of EBS snapshots based on a defined schedule. This helps in taking regular and consistent backups of your EC2 instance's volumes without manual intervention.

## Key Points

- Automation: Schedule Snapshot (Event Bridge) enables you to automate the snapshot creation process. By setting up a schedule, you can define when and how frequently snapshots should be created for your EBS volumes.

- Backup Compliance: Regularly scheduled snapshots help meet backup compliance requirements by ensuring that your data is backed up at predefined intervals. This provides a reliable backup strategy and reduces the risk of data loss.

- Recovery Point Objective (RPO): Scheduled snapshots help define your Recovery Point Objective, which is the point in time to which your data can be restored. By having snapshots at frequent intervals, you can minimize data loss in the event of failures or incidents.

- Cost Optimization: With scheduled snapshots, you can optimize costs by creating backups only when needed. By defining a schedule that aligns with your backup and retention policies, you can avoid unnecessary snapshot creation and associated costs.

## Let's consider an example of a web application running on EC2 instances with EBS volumes. To ensure data protection and minimize data loss, you can set up a scheduled snapshot using Event Bridge.

For instance, you may configure a schedule to create snapshots every hour. This ensures that your application's data is backed up frequently, providing a recovery point in case of accidental data deletion, system failures, or any other unforeseen issues.

By utilizing scheduled snapshots, you can automate the backup process, adhere to backup compliance requirements, and have regular recovery points to restore your application data.

## Implementation Steps

To set up scheduled snapshots using Event Bridge:

1. Launch an EC2 instance and note down the volume ID(s) of the EBS volumes you want to back up.
2. Go to the Event Bridge service in the AWS Management Console.
3. Click on "Create rule" to define a new rule.
4. Enter a name for the rule and select the rule type as "schedule".
5. Configure the schedule pattern to specify the frequency at which snapshots should be created (e.g., every minute, hour, day, etc.).
6. Select the target as "EBS Create Snapshot" and enter the volume ID(s) of the EBS volumes to be included in the scheduled snapshots.
7. Review the rule details and click on "Create rule" to create the scheduled snapshot rule.
8. Monitor the snapshots created based on the defined schedule.
9. After completing your practice, remember to delete the rule, snapshots, and terminate the EC2 instance to avoid unnecessary costs.

Scheduled snapshots using Event Bridge provide a reliable and automated way to back up your EC2 instance's data at regular intervals. This feature helps in maintaining data consistency, meeting compliance requirements, and simplifying your backup and recovery processes.

## Deleting Previous Snapshots

In Scheduling Snapshots using Event Bridge, you have the flexibility to define rules that include deleting previous snapshots to avoid unnecessary costs. For example, if you schedule snapshots every 24 hours, after 5 days, you may have accumulated 5 snapshots. On the 6th day, a new snapshot is created, but you may not require the previous ones.

To manage costs and avoid storing unnecessary snapshots, you can configure your Event Bridge rule to include deleting the previous snapshots when creating a new one. This ensures that only the latest snapshot is retained, minimizing storage costs and reducing clutter in your snapshot inventory.

By defining the rule to delete previous snapshots, you can have an automated and streamlined snapshot management process, where only the most recent snapshot is preserved. This allows you to have a cost-effective backup strategy while still ensuring data protection and recovery capabilities.

It's important to carefully configure the rule to delete previous snapshots according to your retention policies and backup requirements. Be sure to consider factors such as data retention regulations, recovery objectives, and any compliance standards that apply to your workload.

By leveraging the flexibility of Event Bridge in scheduling snapshots and incorporating deletion of previous snapshots, you can effectively manage costs while maintaining a reliable backup strategy for your EC2 instance's volumes.


# Data Lifecycle Manager

Data Lifecycle Manager simplifies the process of managing your data backups in AWS. It allows you to automatically create, retain, and delete EBS snapshots, which are point-in-time copies of your data. Here's a simple explanation with an example:

Imagine you have an important application running on an EC2 instance in AWS. To protect your data, you want to create regular backups. This is where Data Lifecycle Manager comes in. Instead of manually taking backups, you can set up a policy using Data Lifecycle Manager to automate the process.

Let's say you configure a policy to create snapshots every day at midnight and retain them for 7 days. Data Lifecycle Manager will automatically create snapshots of your EC2 instance's volumes at the scheduled time. These snapshots serve as backups, capturing the state of your data at that specific moment.

The snapshots are stored in Amazon S3, a secure and durable storage service provided by AWS. By retaining the snapshots for 7 days, you have multiple recovery points to choose from. For example, if something goes wrong with your application, you can restore your data from any of the snapshots taken within the last 7 days.

Data Lifecycle Manager also helps in cost optimization. After the retention period of 7 days, the older snapshots are automatically deleted. This ensures that you are only storing necessary backups, saving on storage costs.

Additionally, you can use Data Lifecycle Manager to create disaster recovery backup policies. This means you can configure the service to back up your data to separate AWS accounts, providing an extra layer of protection in case of unexpected events.

By automating the creation, retention, and deletion of EBS snapshots with Data Lifecycle Manager, you can ensure the safety and availability of your data, simplify backup management, and optimize costs. It's a valuable tool for maintaining data integrity and meeting compliance requirements in your AWS environment.

## Key Points

- Automated Snapshot Creation: Data Lifecycle Manager enables you to automate the creation of EBS snapshots on a defined schedule. By setting up snapshot policies, you can ensure that your valuable data is regularly backed up without the need for manual intervention.

- Data Protection and Compliance: By enforcing a regular backup schedule, Data Lifecycle Manager helps protect your valuable data. It ensures that backups are retained as required by auditors or internal compliance policies. This helps you meet regulatory requirements and maintain data integrity.

- Cost Optimization: Data Lifecycle Manager helps reduce storage costs by enabling the deletion of outdated backups. You can define retention periods for snapshots, ensuring that only necessary backups are retained, and unnecessary backups are automatically deleted. This helps optimize storage utilization and reduces associated costs.

- Disaster Recovery Backup Policies: With Data Lifecycle Manager, you can create disaster recovery backup policies that back up data to isolated accounts. This provides an additional layer of protection by storing backups in separate AWS accounts, ensuring data availability and resilience in case of unexpected events.

## Using Data Lifecycle Manager

To leverage Data Lifecycle Manager for EBS snapshots, follow these steps:

1. Launch an EC2 instance and create EBS volumes for your data storage needs.
2. Go to the Elastic Block Store (EBS) service in the AWS Management Console.
3. Select the volume for which you want to configure snapshot automation.
4. Add tags to the volume to identify it for lifecycle management purposes.
5. Define the lifecycle management policy by navigating to the Data Lifecycle Manager section in the EBS service.
6. Select the policy type as "EBS Snapshot Policy" and configure the desired settings, including frequency, retention, starting time, and tags.
7. Review the policy details and click on "Create Policy" to create the snapshot policy.
8. Monitor the snapshots created based on the defined schedule in the Data Lifecycle Manager.

By utilizing Data Lifecycle Manager, you can automate the backup process, ensure compliance with retention requirements, optimize storage costs, and enhance your disaster recovery capabilities. The service streamlines snapshot management and provides an efficient solution for protecting and retaining your valuable data.

It's important to configure the lifecycle policies according to your specific backup and retention needs. Consider factors such as data criticality, compliance regulations, recovery objectives, and any industry-specific requirements.

## Difference between Data Lifecycle Manager and Schedule Snapshot (Event Bridge)

The main difference between Data Lifecycle Manager and Schedule Snapshot (Event Bridge) lies in their functionality and how they automate snapshot management.

**Data Lifecycle Manager:** Data Lifecycle Manager is a service provided by AWS that automates the creation, retention, and deletion of EBS snapshots. It allows you to define policies that specify the frequency of snapshot creation, retention periods, and tagging. Data Lifecycle Manager simplifies the process of snapshot management and helps you protect your data, meet compliance requirements, and optimize storage costs.

**Schedule Snapshot (Event Bridge):** Schedule Snapshot (Event Bridge) is a feature within AWS Event Bridge that enables you to schedule the creation of EBS snapshots based on defined schedules. With Schedule Snapshot, you can set up rules specifying when and how frequently snapshots should be created for your EBS volumes. This feature helps you automate the snapshot creation process and ensures regular backups of your data.

In summary, the key difference between Data Lifecycle Manager and Schedule Snapshot (Event Bridge) is the level of automation and flexibility they provide:

- Data Lifecycle Manager offers a comprehensive solution for automating snapshot management with customizable policies for creation, retention, and deletion. It provides more control and allows you to define retention periods, tags, and other configurations.

- Schedule Snapshot (Event Bridge) focuses specifically on automating snapshot creation based on predefined schedules. It simplifies the process of scheduling snapshots without the need for scripting or custom solutions.

Both services aim to automate snapshot management, but Data Lifecycle Manager offers more extensive functionality, while Schedule Snapshot (Event Bridge) provides a simpler and more streamlined approach specifically for snapshot scheduling. The choice between the two depends on your specific requirements and the level of control you need for managing your snapshots.


# Recycle Bin

The Recycle Bin is a feature in Amazon Web Services (AWS) that allows you to store and manage deleted EBS snapshots. It acts as a safeguard against accidental deletion and provides an opportunity to recover deleted snapshots if needed.

## How it Works

When you delete an EBS snapshot, instead of being permanently erased, it is moved to the Recycle Bin. The Recycle Bin acts as a storage area for deleted snapshots, allowing you to retain them for a specified period of time before they are permanently removed.

## Key Points

- Snapshot Protection: The Recycle Bin protects your deleted EBS snapshots from immediate permanent deletion, providing a safety net against accidental data loss.

- Retention Period: You can define a retention period for the snapshots stored in the Recycle Bin. This period determines how long the snapshots remain in the Recycle Bin before they are automatically removed.

- Recovery: If you accidentally delete a snapshot, you can recover it from the Recycle Bin within the defined retention period. This allows you to restore the snapshot and retrieve any data that may have been lost.

## Example and Implementation Steps

Let's consider an example where you have an EC2 machine with an EBS volume, and you want to utilize the Recycle Bin feature.

1. Launch an EC2 instance with an attached EBS volume.
2. Go to the AWS Management Console and navigate to the "Volumes" section.
3. Select the EBS volume associated with your EC2 instance.
4. Click on the "Create Snapshot" option to create a snapshot of the volume.
5. Now, go to the "Snapshots" section and find the created snapshot.
6. Click on the "Recycle Bin" option to move the snapshot to the Recycle Bin.
7. Next, click on "Create Retention Rule" to set up a retention period for the snapshot.
8. Enter a name for the retention rule and select "EBS Snapshot" as the resource type.
9. Check the option to apply the retention rule to all resources.
10. Specify the desired retention period for the snapshot.
11. Click on "Create Retention Rule" to save the rule.
12. To recover a deleted snapshot, go to the EC2 service, select the "Snapshots" section, and find the deleted snapshot.
13. Click on the "Recycle Bin" icon next to the snapshot.
14. Select the snapshot from the list of resources in the Recycle Bin.
15. Click on "Recover" to restore the snapshot.
16. Now, check the "Snapshots" section to verify that the recovered snapshot is available.

By utilizing the Recycle Bin feature, you can protect your deleted EBS snapshots, set retention rules, and recover them if needed. This helps prevent data loss and provides an additional layer of safety for your snapshots.

**Note:** Remember to regularly review and manage the snapshots stored in the Recycle Bin to optimize storage costs and ensure efficient usage of resources.


# Amazon Machine Images (AMI)

Amazon Machine Images (AMIs) are pre-configured templates that contain the necessary software and configurations to launch an instance in Amazon EC2. AMIs provide a convenient way to create instances with specific configurations, including pre-installed software, operating systems, and customizations.

## Key Points

- Instance Customization: You can launch an instance from an existing AMI and customize it according to your requirements. For example, you can install software, configure settings, and make other modifications on the instance.

- Creating Custom AMIs: Once you have customized an instance, you can save its configuration as a custom AMI. This allows you to create new instances with the same customizations, saving time and effort in the setup process.

- Instance Portability: AMIs provide portability, allowing you to move them from one AWS region to another. This means you can create a copy of your instance by copying the AMI to a different region.

- Instance Reboot Condition: When launching an instance from an AMI, you have the option to enable or disable instance reboot during the launch process. If you enable instance reboot, the launched instance will automatically reboot after it finishes launching. This can be useful to ensure that any customizations or configurations applied during instance launch take effect immediately. However, if you disable instance reboot, the launched instance will not reboot automatically.

## Example and Implementation Steps

Let's consider an example where you want to create a custom AMI based on an EC2 instance and utilize it to launch instances in different regions.

1. Create an EC2 instance with the desired configuration and software setup.
2. Create an EBS volume if needed and attach it to the instance.
3. Launch the instance with the specified AMI and perform any necessary customizations.
4. Once the instance is configured as desired, go to the AWS Management Console.
5. Select the instance you want to create an AMI from.
6. Click on the "Actions" button and choose "Image and Templates".
7. Select "Create Image" to create a new AMI.
8. Enter a name and description for the AMI, providing relevant details.
9. Check the "Enable" checkbox to ensure the new AMI is available for launching instances.
10. Click on "Create Image" to create the AMI.
11. Monitor the image creation process and ensure it is successful.
12. Once the AMI is created, you can check it under the "Images" section in the EC2 service.
13. You can also verify that snapshots and volumes associated with the AMI are available.
14. If you want to use the AMI in a different AWS region, select the AMI in the source region.
15. Click on the "Actions" button and choose "Copy AMI".
16. Select the destination region where you want to copy the AMI.
17. Click on "Copy AMI" to start the copying process.
18. Once the AMI is copied to the destination region, you can launch instances using that AMI in the new region.

By utilizing AMIs, you can easily create instances with predefined configurations, customize instances to meet specific requirements, and share AMIs across regions. This helps in streamlining the deployment process, maintaining consistency, and improving scalability and portability of your applications.

## Deletion of AMIs

To delete an AMI, you can navigate to the EC2 service, select the AMI you want to delete, and click on the "Actions" button. From the dropdown menu, choose "Deregister" to remove the AMI from your account. However, note that deleting an AMI does not automatically delete the associated snapshots or EBS volumes. You will need to manually delete those resources if they are no longer needed.

### Steps for Deleting an AMI

1. Go to the EC2 service in the AWS Management Console.
2. Select the AMI you want to delete.
3. Click on the "Actions" button and choose "Deregister" to remove the AMI from your account.

### Handling Associated Snapshots and EBS Volumes

- Deleting an AMI does not automatically delete the associated snapshots or EBS volumes.
- To delete the associated snapshots, go to the "Snapshots" section in the EC2 service, select the relevant snapshots, and choose "Delete" from the "Actions" button.
- To delete the associated EBS volumes, go to the "Volumes" section in the EC2 service, select the relevant volumes, and choose "Delete" from the "Actions" button.

It is important to handle AMIs, associated snapshots, and EBS volumes carefully to manage resources effectively and avoid unnecessary costs. Make sure to review your AMIs and associated resources periodically and delete any that are no longer needed.
