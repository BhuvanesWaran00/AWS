# Establishing a Connection to an Amazon EC2 Instance and Executing Linux Commands

a step-by-step guide on establishing a connection to an Amazon EC2 instance and executing various Linux commands.

## Prerequisites

Before you begin, ensure you have the following:

- An Amazon Web Services (AWS) account.
- An Amazon EC2 instance launched and running.
- The private key (.ppk) file associated with your EC2 instance.
- A terminal or SSH client installed on your local machine.

## connecting Amazon EC2 Instance
### Method 1
- Goto your Ec2 Dashboard 
- click connect 
- Session Manager --> connect
- Now you ready to execute commands
### Method 2
- Goto your Ec2 Dashboard
- Copy Public-Ip Address
- Open Putty or any other terminal emulator application.
- Login With your Public-Ip Address and Private key
- Now you ready to execute commands
## Some Linux Comments
 |CMD	|About Commend| Format|
 |----|----|----|
 |ls| List files and directories in the current directory.|ls|
 |cd| Change the current directory.|cd <destination_path>|
 |pwd| Print the current working directory.|pwd|
 |mkdir| Create a new directory.|mkdir <dir_name>|
 |touch| Create an empty file.|touch <file_name>|
 |uname| Display system information.|uname -a|
 |free| Display memory usage.|free -m|
 |mv|Move files/directories|mv <source> <destination>|
 |rm|Remove files|rm <file>|
 |rmdir|Remove empty directories|rmdir <directory>|
 |ssh|Securely connect to your AWS instances using SSH (Secure Shell) protocol|ssh -i <key_file> <username>@<instance_ip>|
 |aws|The AWS Command Line Interface (CLI) is used to interact with various AWS services from the command line|aws <service> <command> [options]|
 |scp|Securely copy files to and from AWS instances using SSH |scp -i <key_file> <local_file> <username>@<instance_ip><remote_path>|
 |curl|Transfer data with URLs, which is useful for interacting with AWS APIs|curl -X <HTTP_METHOD> <API_URL> -H "Authorization|
 |wget|Download files from the web, which can be useful for fetching data or scripts|wget <url>|
 |rsync|Efficiently synchronize files and directories between local and remote systems|rsync -avz -e "ssh -i <key_file>" <local_dir> <username>@<instance_ip>|
 |scp|Securely copy files between local and remote systems|scp -i <key_file> <local_file> <username>@<instance_ip>|
 |df|Display information about disk space usage on the instance|df -h|
 |top|Monitor system performance and view resource usage in real-time|top|
 |htop|Interactive process viewer, an alternative to top|htop|
 |ps|List currently running processes|ps aux|
 |chmod|Change file permissions |chmod <permissions> <file>|
 |chown|Change file ownership|chown <user>|
 |rep|Search for patterns in files or command output|grep "<pattern>" <file>|
 |tail|Display the last few lines of a file (useful for log files)|tail -n <num_lines> <file>|
 |netstat|Display network statistics and active connections|netstat -tuln|
 |ifconfig|Display or configure network interfaces (deprecated, use ip instead)|ifconfig|
 |ip|Display or configure IP addresses and routes|ip address show|
 |route|Display or manipulate the IP routing table|route -n|
