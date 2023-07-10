# Difference between Block Storage and Object level storage
# Elastic Block Store
Whenever we are creating EC2 machine, the volume we are getting with ec2 machine are called as root/boot volume also called as EBS volume.

EBS volume are persistent volume mean whenever you stop or reboot your Ec2 instance, your data will not delete. Your data will only delete in case of termination of EC2 instance.

**DeleteOnTermination**- Delete on Termination means whenever you are deleting EC2 machine then that time do you want to delete your volume. 

By default, the DeleteOnTermination attribute is set to True for the root volume. It is set to False for all other volume types.

**What is the Purpose of Elastic Block Storage**<br/>
  Amazon EBS allows you to create storage volumes and attach them to Amazon EC2 instances. Once attached, you can create a file system on top of these volumes, run a database, or use them in any other way you would use block storage. 

**Let's create the Elastic Block Storage on Linux based Operating System**

1. Create linux EC2 machine 

2. Add 5GB extra volume from configure storage

3. check delete on Termination

4. Launch the instance

5. Go to volumes and check attached extra volume. There you will find two volumes 1. The default 8GB volume 2. The additional 5GB volume.

6. Connect to linux EC2 machine with putty client.

7. Use linux command to check whatever the harddisk is linked to this particular EC2 machine - df -Th

**NOTE** - There you will not able to find your additional 5GB volume.Reason is we have attched the volume, we didn't mount it. You need to first mount it.

8. To check the attached volume - lsblk<br/>
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

**This is how we added the additional volume with EC2 machine**

**Now if the requirement come where you have to detach the additional volume from one EC2 instance and attach it to another EC2 instance without losing the data in that volume**

14. First I have to detach the volume from one EC2 machine
        sudo umount test

15. Run df -Th, you will not find the mount volume because you have unmounted it.

16. Now we need to detach the volume from our console<br/>
     go to volumes.<br/>
     select 5GB to detach volume<br/>
     click on Action button on the top right then click on detach volume.

**Note** - Whenever you attach existing volume to new EC2 machine make sure EC2 machine and existing volume needs to be in same availability zone.If your existing volume in another avialability zone and your new EC2 instance is another avialability zone then it is imposible to attach volume .

17. Now I am creating EC2 machine in the same availability zone.<br/>
    Create linux EC2 machine<br/>
    go to network and settings, there you can select the availability zone . It is mandatory so that this machine will create in same avialability zone as my volume.<br/>
    Now launch the EC2 machine<br/>

18. Now we have to attach the existing volume to new EC2 machine.
     go to volumes.<br/>
     select 5GB to attach volume<br/>
     click on Action button on the top right then click on attach volume.

19. Now connect the new EC2 machine with putty client.

20. Now again I am trying df -Th command, you will not able to see the 5GB additional volume. Again we need to mount the volume.

21. To mount the volume. I need the volume name . We will chcek from lsblk command<br/>
    Note down the volume name.

22. Now Again I am going to create one another directory<br/>
    mkdir training

23. With this particular folder, I am going to mount the volume<br/>
    sudo mount /dev/xvdf training

24. change directory to training<br/>
    cd training

25. list the files - ls<br/>
    you will able to find all files which you have created in test volume.

**Note**- Previously we have created 3 files under test folder. Now we will check if we are able to see those files under training directory. You will get all those files because the files which we have created, we were not created in test folder, the files was there in volume(harddisk). 


**Let's create the Elastic Block Storage on Windows based Operating System**

In this we will do the same example which we have done above with Linus based OS. Here we will first add additional volume with the EC2 machine then in next step we will detach the existing volume and attach the volume to new EC2 machine.

1. Go to EC2 and create windows based EC2 machine.

2. Add 5GB extra volume from configure storage and launch instances.

3. Now create second machine without additional volume.

4. Now connect to first windows machine

5. After connecting to first windows machine. Go to this PC. There you will not able to see 5GB additional volume beacuse the volume we have just added not mounted.

6. To mounting the volume to windows EC2 machine we have to go to "server manager". Click on window button and type server manager.

7. In server manager you will see role " File and Storage". With the help of file and storage we will mount the volume.

8. click on File and Storage. Click on "Disk". You will find your 5GB additional volume with "offline" stataus. We have to bring it "online".

9. Select this 5GB volume, right click and select " bring online"

10. Right click on volume again and click on "Initialize".

11. Again right click on volume select new volume. Now one prompt will open where you have to specify the size of volume, name of drive and create.

12. Check in this PC you will find additional volume of 5GB.

13. create one notepad file in 5GB volume.

14. Now mount the same volume to second Windows EC2 machine.<br/>
    Before that we have to unmount the volume from First EC2 machine.

15. Go to " server manager", clisk on disk, clisk on 5GB volume and bring offline.You have umnounted it now

16. Next we have to detach the volume<br/>
    Go to console, go to volume, select volume, click on Action and detach volume.

17. Now we have to attach this existing volume to second EC2 machine<br/>
    Go to volume, click on Action, attach volume to second EC2 machine.

18. Now connect to second EC2 machine.Go to Server Mananger. Select this 5GB volume, right click and select " bring online".

19. Now check this PC you will get additional volume with same notepad file and with same content.

**This is how we are creating EBS volume and attcahing the same volume to another EC2 machine**













    




 
     