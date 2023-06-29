# DAY 2: Introduction to Linux and Linux Commands

In Day 1, we explored cloud computing, learned how to create an AWS account, and created Windows and Ubuntu EC2 instances. We also learned how to connect to EC2 instances from our local computer. Now, before we dive into new topics, let's first familiarize ourselves with Linux and Linux commands, as they form the backbone of DevOps.

## :penguin: What is Linux?

Linux is an open-source operating system that forms the foundation of many cloud platforms, servers, and devices. It provides a powerful and flexible environment for software development, system administration, and automation.

### :computer: Where to Run Linux Commands?

To run Linux commands, we use the **Terminal** or **Command Line Interface (CLI)**. The Terminal allows us to interact with the Linux operating system by typing commands and receiving output.

- **For Windows Users:** To run Linux commands on Windows, you can use a terminal emulator such as **Git Bash**, **Windows Subsystem for Linux (WSL)**, or **PuTTY**.

- **For macOS Users:** The macOS operating system already includes a built-in terminal application called **Terminal**. You can launch it from the "Utilities" folder within the "Applications" directory.

- **For Linux Users:** If you are using a Linux distribution as your primary operating system, you can access the terminal directly from the desktop environment or use the shortcut keys **Ctrl + Alt + T** to open the terminal.

### :floppy_disk: Example of Linux Operating Systems

Here are some examples of popular Linux operating systems:

- Amazon Linux
- Ubuntu
- CentOS
- Red Hat Enterprise Linux

### :computer: Linux Commands

Linux commands are the building blocks of executing tasks and managing the Linux operating system. They allow us to perform a wide range of operations, such as navigating the file system, managing processes, installing software, and configuring system settings.

## :notebook_with_decorative_cover: Why Learn Linux and Linux Commands?

Understanding Linux and mastering Linux commands are crucial for DevOps practitioners. Here's why:

- **Compatibility:** Linux is widely used in the DevOps ecosystem, and many tools and technologies are designed to work seamlessly with Linux-based systems.
- **Automation:** Linux commands play a vital role in automating tasks and creating efficient workflows using scripting languages like Bash.
- **Server Administration:** Linux is prevalent in server environments, and knowing how to manage and troubleshoot Linux servers is essential for DevOps professionals.
- **Containerization and Orchestration:** Linux-based technologies like Docker and Kubernetes are widely used for containerization and orchestration, enabling scalable and portable deployments.

# Types of Linux Commands

Linux commands can be broadly categorized into different types based on their functionality. Understanding these command types will help you navigate and leverage the power of the Linux command line effectively. Here are some common types of Linux commands:

## System Commands

System commands provide information about the system, manage system settings, and perform system-related operations. Here are a few examples: 

- **uname**: Displays system information such as the kernel version, machine architecture, and operating system.
  - Example: `uname -a`

- **date**: Shows the current date and time on the system.
  - Example: `date`

- **shutdown**: Allows you to gracefully shut down or restart the system.
  - Example: `shutdown -h now` (shutdown the system immediately)

- **free**: Displays information about the system's memory usage, including total, used, and free memory.
  - Example: `free -h` (displays memory usage in human-readable format)

- **top**: Provides a real-time, dynamic view of system processes, CPU usage, and memory usage.
  - Example: `top`

- **df**: Displays disk space usage of file systems, including total, used, and available space.
  - Example: `df -h` (displays disk usage in human-readable format)

- **du**: Estimates file and directory sizes, showing the disk space used by each.
  - Example: `du -sh /path/to/directory` (displays the total size of the directory)

- **ps**: Provides information about currently running processes on the system.
  - Example: `ps aux` (displays all running processes in a detailed format)

- **kill**: Terminates a running process by its process ID (PID).
  - Example: `kill 1234` (terminates the process with PID 1234)

- **history**: Displays a list of previously executed commands in the terminal.
  - Example: `history`

## File Management Commands

File management commands allow you to create, delete, copy, move, and modify files and directories. Let's look at some commonly used file management commands:

- **ls**: Lists files and directories in the current directory.
  - Example: `ls`

- **cp**: Copies files and directories from one location to another.
  - Example: `cp file.txt /path/to/destination`

- **mv**: Moves or renames files and directories.
  - Example: `mv file.txt /path/to/destination` (move)
  - Example: `mv file.txt newfile.txt` (rename)

- **rm**: Removes (deletes) files and directories.
  - Example: `rm file.txt` (remove a file)
  - Example: `rm -r directory` (remove a directory and its contents)

- **mkdir**: Creates a new directory.
  - Example: `mkdir newdir`

- **rmdir**: Removes an empty directory.
  - Example: `rmdir emptydir`

- **touch**: Creates an empty file or updates the timestamp of an existing file.
  - Example: `touch file.txt`

- **cat**: Concatenates and displays the contents of one or more files.
  - Example: `cat file.txt`

- **less**: Allows paging through the contents of a file.
  - Example: `less file.txt`

- **head**: Displays the first few lines of a file.
  - Example: `head file.txt`

- **tail**: Displays the last few lines of a file.
  - Example: `tail file.txt`

- **grep**: Searches for a specific pattern in one or more files.
  - Example: `grep "pattern" file.txt`

- **chmod**: Changes file permissions (read, write, execute) for a file or directory.
  - Example: `chmod 755 file.txt` (gives read, write, and execute permissions to the owner)

- **chown**: Changes the ownership of a file or directory.
  - Example: `chown user:group file.txt` (changes the ownership to a specific user and group)

- **find**: Searches for files and directories based on various criteria.
  - Example: `find /path/to/search -name "file.txt"` (searches for a file by name)

## Process Management Commands

Process management commands help you manage processes running on the system. You can start, stop, monitor, and control processes using these commands. Here are a few examples:

- **ps**: Displays information about running processes.
  - Example: `ps aux` (displays a detailed list of all processes)

- **top**: Provides a dynamic real-time view of the system's processes.
  - Example: `top` (displays continuously updating process information)

- **htop**: Interactive process viewer, an alternative to top with more features.
  - Example: `htop` (displays an interactive process monitoring interface)

- **kill**: Terminates a process by sending a signal.
  - Example: `kill <PID>` (sends the default SIGTERM signal to the process with the specified PID)

- **killall**: Terminates processes by name.
  - Example: `killall firefox` (terminates all running instances of the Firefox browser)

- **pgrep**: Lists the PIDs of processes based on criteria.
  - Example: `pgrep -u username` (lists the PIDs of processes owned by a specific user)

- **pkill**: Sends a signal to processes based on criteria.
  - Example: `pkill -u username` (sends the default SIGTERM signal to processes owned by a specific user)

- **nice**: Sets the priority of a process.
  - Example: `nice -n 10 command` (runs a command with a lower priority value of 10)

- **renice**: Changes the priority of running processes.
  - Example: `renice +5 -p <PID>` (increases the priority of the process with the specified PID by 5)

- **systemctl**: Controls the systemd system and service manager.
  - Example: `systemctl start service` (starts a systemd service)



## Networking Commands

Networking commands enable you to manage network interfaces, troubleshoot network issues, and perform various network-related tasks. Let's explore some commonly used networking commands:

- **ifconfig**: Displays and configures network interfaces.
  - Example: `ifconfig eth0` (displays information about the network interface "eth0")

- **ip**: Provides advanced IP configuration and routing information.
  - Example: `ip address show` (displays IP addresses assigned to network interfaces)

- **ping**: Sends ICMP echo requests to a network host to check connectivity.
  - Example: `ping 8.8.8.8` (sends ICMP echo requests to the IP address 8.8.8.8)

- **nslookup**: Queries DNS servers to retrieve DNS information.
  - Example: `nslookup example.com` (performs a DNS lookup for the domain "example.com")

- **traceroute**: Traces the route that packets take to reach a network host.
  - Example: `traceroute google.com` (traces the route to the host "google.com")

- **netstat**: Displays network statistics and active connections.
  - Example: `netstat -tuln` (shows TCP and UDP connections with associated ports)

- **ss**: Provides information about network sockets.
  - Example: `ss -tunap` (displays TCP and UDP sockets and their corresponding processes)

- **ssh**: Securely connects to a remote system using the SSH protocol.
  - Example: `ssh user@example.com` (establishes an SSH connection to the host "example.com" as the user "user")

- **wget**: Downloads files from the web using various protocols.
  - Example: `wget http://example.com/file.txt` (downloads the file "file.txt" from the URL "http://example.com")

- **curl**: Transfers data to or from a network server using various protocols.
  - Example: `curl -O http://example.com/file.txt` (downloads the file "file.txt" from the URL "http://example.com")


## Package Management Commands

Package management commands facilitate the installation, removal, and management of software packages on Linux distributions. Here are a few examples:

- **apt**: Advanced Package Tool for Debian-based systems.
  - Example: `apt update` (updates the package list)

- **apt-get**: Command-line package handling utility for Debian-based systems.
  - Example: `apt-get install package_name` (installs a package)

- **apt-cache**: Query the package cache of Debian-based systems.
  - Example: `apt-cache search keyword` (searches for packages containing the keyword)

- **aptitude**: Text-based interface for package management on Debian-based systems.
  - Example: `aptitude upgrade` (upgrades installed packages)

- **dpkg**: Low-level package management command for Debian-based systems.
  - Example: `dpkg -i package.deb` (installs a .deb package)

- **dpkg-query**: Query the package database of Debian-based systems managed by dpkg.
  - Example: `dpkg-query -l package_name` (checks if a package is installed)

- **yum**: Package manager for RPM-based systems (such as CentOS and Fedora).
  - Example: `yum install package_name` (installs a package)

- **dnf**: Next-generation package manager, a successor to yum.
  - Example: `dnf update` (updates the system packages)

- **rpm**: Package manager for RPM-based systems, used for installing, querying, and verifying packages.
  - Example: `rpm -qa` (lists all installed packages)

- **zypper**: Package manager for openSUSE and SUSE Linux Enterprise systems.
  - Example: `zypper install package_name` (installs a package)

- **dnf-automatic**: Automates package updates on systems using dnf.
  - Example: `dnf-automatic --installupdates` (automatically installs available updates)

- **pip**: Package installer for Python packages.
  - Example: `pip install package_name` (installs a Python package)

## Text Processing Commands

Text processing commands enable you to manipulate and analyze text files. They can perform operations such as searching, replacing, sorting, and filtering text. Let's explore a few popular text processing commands:

- **grep**: Search for patterns in files.
  - Example: `grep "pattern" file.txt` (searches for lines containing the specified pattern in the file)

- **sed**: Stream editor for text manipulation.
  - Example: `sed 's/old/new/g' file.txt` (replaces all occurrences of "old" with "new" in the file)

- **awk**: Text processing language for extracting and manipulating data.
  - Example: `awk '{print $1}' file.txt` (prints the first field of each line in the file)

- **sort**: Sort lines of text.
  - Example: `sort file.txt` (sorts the lines in the file in ascending order)

- **cut**: Extract specific columns or fields from text.
  - Example: `cut -f1,3 file.txt` (extracts the first and third columns from the file)

- **tr**: Translate or delete characters.
  - Example: `tr 'a-z' 'A-Z' < file.txt` (converts lowercase letters to uppercase in the file)

- **head**: Output the first part of files.
  - Example: `head -n 10 file.txt` (displays the first 10 lines of the file)

- **tail**: Output the last part of files.
  - Example: `tail -n 5 file.txt` (displays the last 5 lines of the file)

- **uniq**: Report or omit repeated lines.
  - Example: `uniq file.txt` (removes consecutive duplicate lines from the file)

- **wc**: Print word, line, and byte counts.
  - Example: `wc -l file.txt` (displays the number of lines in the file)

## User Management Commands

User management commands allow you to create, modify, and manage user accounts on the system. Here are some commonly used user management commands:

- **useradd**: Create a new user.
  - Example: `useradd john` (creates a new user named "john")

- **passwd**: Change user password.
  - Example: `passwd john` (prompts to change the password for the user "john")

- **usermod**: Modify user settings.
  - Example: `usermod -aG sudo john` (adds the user "john" to the "sudo" group)

- **userdel**: Delete a user account.
  - Example: `userdel john` (deletes the user account "john")

- **whoami**: Display the current user.
  - Example: `whoami` (displays the username of the current user)

- **su**: Switch user.
  - Example: `su john` (switches to the user account "john")

- **root**: Superuser account.
  - Example: `root` (refers to the superuser account with administrative privileges)

- **su**: Switch to root user.
  - Example: `su -` (switches to the root user account with full privileges)

- **chown**: Change file ownership.
  - Example: `chown john:users file.txt` (changes the owner and group of "file.txt" to "john" and "users")

- **chgrp**: Change group ownership.
  - Example: `chgrp staff file.txt` (changes the group ownership of "file.txt" to "staff")

These are just a few examples of the diverse range of Linux commands available. As you progress in your Linux journey, you will encounter many more commands and become familiar with their usage.

## :books: Learning Resources

To kickstart our Linux learning journey, here are some recommended resources:

- :white_check_mark: [Linux Command Line Basics](https://www.learnshell.org/) - An interactive online tutorial to learn the basics of Linux commands.
- :white_check_mark: [Linux Journey](https://linuxjourney.com/) - A comprehensive tutorial that covers various aspects of Linux, from basic commands to system administration.
- :white_check_mark: [The Linux Documentation Project](https://www.tldp.org/guides.html) - A collection of guides and how-tos on different Linux topics.

Let's embrace the power of Linux and dive deeper into the world of DevOps!

## :rocket: Next Steps

In the upcoming days, we will explore various DevOps tools, practices, and methodologies. Stay tuned for Day 3, where we will delve into the world of version control with Git and GitHub.

Remember, consistency and continuous learning are key to mastering DevOps. Let's keep pushing ourselves to grow and collaborate along this exciting journey!

Feel free to share your thoughts, ask questions, and provide feedback in the comments section below. Let's learn and grow together! :muscle:

Keep Learning, Keep Growing! :seedling: 

Best Regards,
[Your Name]
