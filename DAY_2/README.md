# DAY 2: Transferring Files to a Server using SCP and Essential Linux Commands

In this folder, we will explore two topics: transferring files to a server using the SCP (Secure Copy) command and a selection of commonly used Linux commands.

## :arrow_up: Transferring Files to a Server using SCP Command

scp (Secure Copy) is a command-line utility in Linux that allows you to securely transfer files between your local machine and a remote server. It uses the SSH protocol for secure data transfer.

To transfer a file from your local machine to a remote server using SCP, follow these steps:

1. Connect EC2 Linux and open a terminal or command prompt on your local machine.
2. Use the following syntax to copy a file to the server:

scp /path/to/local/file username@server_ip:/path/on/server

- Replace `/path/to/local/file` with the path to the file you want to transfer.
- Replace `username` with your username on the remote server.
- Replace `server_ip` with the IP address or hostname of the remote server.
- Replace `/path/on/server` with the destination path on the remote server where you want to save the file.
3. If the remote server requires a specific port for SSH, you can specify it with the `-P` option:

4. Enter your password when prompted. If you have set up SSH key-based authentication, you may not be prompted for a password.

Note: SCP also supports transferring directories by adding the `-r` flag before the source directory.

## :penguin: Essential Linux Commands

Linux provides a rich set of command-line utilities that can greatly enhance your productivity as a DevOps engineer. 

It is an open source operating system (OS). An operating system is the software that directly manages a system’s hardware and resources, like CPU, memory, and storage.

Here are some commonly used Linux commands:

To create a file : cat > <File_Name>
To list of Files Created : ls
To read the File Content : cat <File_name>
To remove a file : rm <file_Name>
To create a directory : mkdir <Directory_Name>
To check the current path : pwd
To change Directory : cd <Directory_Name>
To go to Previous directory : cd ..
To delete a directory with files : rm -r <Directory_Name>
To create hidden directory : touch .<File_Name>
To see hidden files : ls –a
To create copy of a file : cp <Source_File_Name> <Destination_file_Name>
To check current user : Whoami
To see the list of files according to timestamp : ls -lt
To get the current date : date
To change the file permissions : chmod (Change Mode)
There are two ways we can change permission of our files
Absolute Mode (Numerical)
Symbolic Mode (Alphabetical)

## Absolute Mode (Numerical) 

<img src="https://github.com/shreya-singh21/60-DAYS-DEVOPS-CHALENGE/blob/master/Images/absolute_mode.PNG" width="700">
 
 Ex- chmod 764 <File_Name>

## Symbolic Mode (Alphabetical)

<img src="https://github.com/shreya-singh21/60-DAYS-DEVOPS-CHALENGE/blob/master/Images/symbolic_mode.PNG" width="700">

Ex- chmod u+r,g+w,o+x <file_name>

YUM Repository
An YUM Repository is a collection of packages. YUM Repository allows you to perform package install, removal, upgrade operations on individual packages.In Red hat also, it is called YUM Repository & in Ubuntu is called as APT Repository.

To install the packages from YUM repository
Step1: Update YUM Repository
Step2: Install the Package

To update YUM Repository : sudo YUM update
To install the Package : sudo YUM install <package_name>

To edit the File : vi <File_name>

In vi command there are two modes:
Command Mode
Insert Mode
By Default, system will open the file in command mode. Change to insert mode
Press i
Now edit the file
To save the file : Press Esc
To save and exit : :wq!
To exit without saving : :q!


This list represents just a small fraction of the extensive range of Linux commands available. Feel free to explore the Linux command-line ecosystem further to enhance your proficiency as a DevOps engineer.

## :books: Additional Resources

- [SCP command documentation](https://manpages.ubuntu.com/manpages/latest/en/man1/scp.1.html)
- [Linux command-line cheat sheet](https://cheatography.com/davechild/cheat-sheets/linux-command-line/)

Take advantage of these resources to deepen your understanding of file transfer using SCP and expand your knowledge of essential Linux commands.

Happy learning and enjoy your DevOps journey!

