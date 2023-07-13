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

**Note** - In EFS you are creating files in common shared location and anyone can access it from anywhere .


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


