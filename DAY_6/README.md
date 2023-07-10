# Difference between Block Storage and Object level storage
# Elastic Block Store
Whenever we are creating EC2 machine, the volume we are getting with ec2 machine are called as root/boot volume also called as EBS volume.

EBS volume are persistent volume mean whenever you stop or reboot your Ec2 instance, your data will not delete. Your data will only delete in case of termination of EC2 instance.

**DeleteOnTermination**- Delete on Termination means whenever you are deleting EC2 machine then that time do you want to delete your volume. 

By default, the DeleteOnTermination attribute is set to True for the root volume. It is set to False for all other volume types.

**Purpose** - Amazon EBS allows you to create storage volumes and attach them to Amazon EC2 instances. Once attached, you can create a file system on top of these volumes, run a database, or use them in any other way you would use block storage. 

1. Create linux EC2 machine 

2. Add 5GB extra volume from add storage

3. check delete on Termination

4. Launch the instance

5. Go to volumes and check attached extra volume. There you will find two volumes 1. The default 8GB volume 2. The additional 5GB volume.

6. Connect to linux EC2 machine.

7. Use linux command to check whatever the harddisk is linked to this particular EC2 machine - df -Th

**NOTE** - There you will not able to find your additional 5GB volume.Reason is we have attched the volume, we didn't mount it. You need to first mount it.

8. To check the attached volume - lsblk
**Note** - There you will able to find your both volumes. 

8. We have to mount the volume. <br/>
   1. Note down the additional volume name from above command. My case it is xvdb. It may change in your case.
   2. To mount any volume we need to create file system and in cloud platform ext4 file system is supported.
       sudo mkfs -t ext4 /dev/xvdf

9. Now create on directory with any name
       mkdir test 

10. Attach this particular folder with volume
       sudo mount /dev/xvdf test

11. Now change directory
       cd test

**Note** - Till now we have added extra volume, we mounted it, we created folder, attached the folder to volume.<BR/>
           As per AWS whatever we do with this folder it will reflect in the volume so we are actually accessing the volume.

12. Now I am creating files in test folder
        sudo touch file1 file2 file3

13. Now run the same command to check mount point - df -Th<BR/>
    This time you will able to see the additional volume with path.

**This is how we add the additional volume with EC2 machine**

git
 
     