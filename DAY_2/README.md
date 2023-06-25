# DAY 2: Transferring Files to a Server using SCP and Essential Linux Commands

In this folder, we will explore two topics: transferring files to a server using the SCP (Secure Copy) command and a selection of commonly used Linux commands.

## :arrow_up: Transferring Files to a Server using SCP Command

scp (Secure Copy) is a command-line utility in Linux that allows you to securely transfer files between your local machine and a remote server. It uses the SSH protocol for secure data transfer.

To transfer a file from your local machine to a remote server using SCP, follow these steps:

1. Open a terminal or command prompt on your local machine.
2. Use the following syntax to copy a file to the server:

- Replace `/path/to/local/file` with the path to the file you want to transfer.
- Replace `username` with your username on the remote server.
- Replace `server_ip` with the IP address or hostname of the remote server.
- Replace `/path/on/server` with the destination path on the remote server where you want to save the file.
3. If the remote server requires a specific port for SSH, you can specify it with the `-P` option:

4. Enter your password when prompted. If you have set up SSH key-based authentication, you may not be prompted for a password.

Note: SCP also supports transferring directories by adding the `-r` flag before the source directory.

## :penguin: Essential Linux Commands

Linux provides a rich set of command-line utilities that can greatly enhance your productivity as a DevOps engineer. Here are some commonly used Linux commands:

- **ls:** List files and directories.
- **cd:** Change directory.
- **pwd:** Print the current working directory.
- **mkdir:** Create a new directory.
- **rm:** Remove files and directories.
- **cp:** Copy files and directories.
- **mv:** Move or rename files and directories.
- **cat:** Display the contents of a file.
- **grep:** Search for a pattern in files.
- **find:** Search for files and directories.
- **chmod:** Change file permissions.
- **chown:** Change file ownership.
- **tar:** Create or extract tar archives.
- **top:** Display system resource usage and running processes.
- **ps:** Display information about active processes.
- **ssh:** Connect to a remote server using the SSH protocol.
- **sudo:** Execute a command with superuser privileges.

This list represents just a small fraction of the extensive range of Linux commands available. Feel free to explore the Linux command-line ecosystem further to enhance your proficiency as a DevOps engineer.

## :books: Additional Resources

- [SCP command documentation](https://manpages.ubuntu.com/manpages/latest/en/man1/scp.1.html)
- [Linux command-line cheat sheet](https://cheatography.com/davechild/cheat-sheets/linux-command-line/)

Take advantage of these resources to deepen your understanding of file transfer using SCP and expand your knowledge of essential Linux commands.

Happy learning and enjoy your DevOps journey!

