# Establishing a Connection to an Amazon EC2 Instance and Executing Linux Commands

A step-by-step guide on establishing a connection to an Amazon EC2 instance and executing various Linux commands.

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
 |CMD	|About Commend| Format|Example|
 |----|----|----|----|
 |ls| List files and directories in the current directory.|ls|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267602815-3d826a57-80ce-44cc-9466-158e8b663dc9.png" target="_blank">ctrl + Click hear</a>|
 |cd| Change the current directory.|cd <destination_path>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605975-f7f32604-3ee2-4e30-a24a-af2a01e0435c.png" target="_blank">ctrl + Click hear</a>|
 |pwd| Print the current working directory.|pwd|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605921-3389c113-4f3b-49ad-b3be-30fb00482bd8.png" target="_blank">ctrl + Click hear</a>|
 |mkdir| Create a new directory.|mkdir <dir_name>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267602815-3d826a57-80ce-44cc-9466-158e8b663dc9.png" target="_blank">ctrl + Click hear</a>|
 |touch| Create an empty file.|touch <file_name>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605963-ea35cf28-8218-4649-a303-36cf2af2a3bd.png" target="_blank">ctrl + Click hear</a>|
 |uname| Display system information.|uname -a|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605967-c85f71aa-3eca-45d3-ba68-b81bb36a604f.png" target="_blank">ctrl + Click hear</a>|
 |free| Display memory usage.|free -m|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605992-6fef7c04-957a-4a0c-bb39-6dbc0891e067.png" target="_blank">ctrl + Click hear</a>|
 |mv|Move files/directories|mv <source> <destination>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267606021-93fcc9f7-0ba9-4e0a-95b6-612648cf4386.png" target="_blank">ctrl + Click hear</a>|
 |rm|Remove files|rm <file>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605927-97f6a860-f461-4a12-88be-e9b3ef9f1c35.png" target="_blank">ctrl + Click hear</a>|
 |rmdir|Remove empty directories|rmdir <directory>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605930-61949d17-35a3-41f7-b1cc-a7321e4b5a48.png" target="_blank">ctrl + Click hear</a>|
 |ssh|Securely connect to your AWS instances using SSH (Secure Shell) protocol|ssh -i <key_file> <username>@<instance_ip>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605947-39ec78c3-b046-47d3-a4a4-b649f0844c4e.png" target="_blank">ctrl + Click hear</a>|
 |aws|The AWS Command Line Interface (CLI) is used to interact with various AWS services from the command line|aws <service> <command> [options]|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605972-5d0bbb57-d290-41ec-b90e-661e17cacb39.png" target="_blank">ctrl + Click hear</a>|
 |curl|Transfer data with URLs, which is useful for interacting with AWS APIs|curl -X <HTTP_METHOD> <API_URL> -H "Authorization|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605986-4ec8a5bc-3d7d-4612-8e40-f34121eb16f3.png" target="_blank">ctrl + Click hear</a>|
 |wget|Download files from the web, which can be useful for fetching data or scripts|wget <url>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605970-3e512e6d-f134-48d8-acc8-80f26c6d7958.png" target="_blank">ctrl + Click hear</a>|
 |rsync|Efficiently synchronize files and directories between local and remote systems|rsync -avz -e "ssh -i <key_file>" <local_dir> <username>@<instance_ip>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605938-9febadac-ddc8-4787-b290-dbb11d19ee0b.png" target="_blank">ctrl + Click hear</a>|
 |scp|Securely copy files between local and remote systems|scp -i <key_file> <local_file> <username>@<instance_ip>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605941-14620d42-dfd7-45a7-a3b1-ef51f144ee44.png" target="_blank">ctrl + Click hear</a>|
 |df|Display information about disk space usage on the instance|df -h|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605988-344695fe-dc6b-415a-98f1-ea27b7781222.png" target="_blank">ctrl + Click hear</a>|
 |top|Monitor system performance and view resource usage in real-time|top|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605959-8df39992-f943-4bb8-b64d-c3b115a6e0d4.png" target="_blank">ctrl + Click hear</a>|
 |htop|Interactive process viewer, an alternative to top|htop|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267606001-95227303-d1cd-4c8d-84d8-b11ea229cd94.png" target="_blank">ctrl + Click hear</a>|
 |ps|List currently running processes|ps aux|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267613991-cf206f6e-fe22-4d9d-b563-a95fb20f1761.png" target="_blank">ctrl + Click hear</a>|
 |chmod|Change file permissions |chmod <permissions> <file>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605979-0e039efd-d85a-4edb-a8d1-e37aaea6230b.png" target="_blank">ctrl + Click hear</a>|
 |chown|Change file ownership|chown <user>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605982-6f6f3eed-f6b5-4ad0-9b03-c0a9cb8cfe4f.png" target="_blank">ctrl + Click hear</a>|
 |grep|Search for patterns in files or command output|grep "<pattern>" <file>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605996-0a7c18ef-b873-44d6-81ac-ce75fb243a37.png" target="_blank">ctrl + Click hear</a>|
 |tail|Display the last few lines of a file (useful for log files)|tail -n <num_lines> <file>|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605953-368cd4d7-b227-4e5b-b27a-1680ac09a3b5.png" target="_blank">ctrl + Click hear</a>|
 |netstat|Display network statistics and active connections|netstat -tuln|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267606025-5b705a70-54c6-4386-a837-685fb412d77b.png" target="_blank">ctrl + Click hear</a>|
 |ifconfig|Display or configure network interfaces (deprecated, use ip instead)|ifconfig|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267606007-4c63c100-979e-43aa-94b8-4cc5b1977c81.png" target="_blank">ctrl + Click hear</a>|
 |ip|Display or configure IP addresses and routes|ip address show|<a href="" target="_blanhttps://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267606012-39d74765-e1ce-4a84-845d-004e76165684.pngk">ctrl + Click hear</a>|
 |route|Display or manipulate the IP routing table|route -n|<a href="https://github-production-user-asset-6210df.s3.amazonaws.com/117109051/267605933-c8b1e5e5-71fc-42f8-83d5-4a0ebba48de5.png" target="_blank">ctrl + Click hear</a>|
