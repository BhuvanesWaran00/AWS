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
1. **Command: `sudo`**
   - Description: Change User root
   - Usage: `sudo su`<br>
     ![1 sudo](https://github.com/BhuvanesWaran00/AWS/assets/117109051/ae5880e2-3f0b-425f-89c4-1d54cd8ced73)

2. **Command: `uname`**
   - Description: Display system information.
   - Usage: `uname -a`<br>
     ![2 uname](https://github.com/BhuvanesWaran00/AWS/assets/117109051/a534cee7-f066-4571-ab8c-381a357ff2d9)


### Memory Commands

3. **Command: `free`**
   - Description: Display memory usage.
   - Usage: `free`<br>
     ![3 free](https://github.com/BhuvanesWaran00/AWS/assets/117109051/4e672ad1-511e-450d-97eb-3c091859c8cf)


4. **Command: `df`**
    - Description: Display information about disk space usage on the instance.
    - Usage: `df -h`<br>
      ![4 df](https://github.com/BhuvanesWaran00/AWS/assets/117109051/5a7be5cf-62da-4d76-a5d5-5d6b95302e26)


### Network Commands

5. **Command: `netstat`**
    - Description: Display network statistics and active connections.
    - Usage: `netstat -tuln`<br>
      ![5 netstat](https://github.com/BhuvanesWaran00/AWS/assets/117109051/8e142d3f-228e-4881-b459-f9dd078d40a9)


6. **Command: `ifconfig`**
    - Description: Display or configure network interfaces (deprecated, use `ip` instead).
    - Usage: `ifconfig`<br>
      ![6 ifconfig](https://github.com/BhuvanesWaran00/AWS/assets/117109051/67bb073e-1816-4cd6-ad52-4c48ca240211)

    

7. **Command: `ip`**
    - Description: Display or configure IP addresses and routes.
    - Usage: `ip address show`<br>
      ![7 ip](https://github.com/BhuvanesWaran00/AWS/assets/117109051/2ec2bc9e-18b6-499e-ad38-7754c56309f4)


8. **Command: `route`**
    - Description: Display or manipulate the IP routing table.
    - Usage: `route -n`<br>
      ![8 route](https://github.com/BhuvanesWaran00/AWS/assets/117109051/392bba72-3feb-452b-86f5-a8c4d95c6fa0)

    
9. **Command: `mkdir`**
   - Description: Create a new directory.
   - Usage: `mkdir <dir_name>`<br>
   

10. **Command: `cd`**
    - Description: Change the current directory.
    - Usage: `cd <destination_path>`<br>
    

11. **Command: `pwd`**
    - Description: Print the current working directory.<br>
    

12. **Command: `touch`**
    - Description: Create an empty file.
    - Usage: `touch <file_name>`<br>
    

13. **Command: `ls`**
    - Description: List files and directories in the current directory.<br>
    

14. **Command: `rm`**
    - Description: Remove files.
    - Usage: `rm <file>`<br>
    

15. **Command: `rmdir`**
    - Description: Remove empty directories.
    - Usage: `rmdir <directory>`<br>
      ![9-15 pwd](https://github.com/BhuvanesWaran00/AWS/assets/117109051/2c7761f9-665d-4e7f-904b-f1b4f87a6116)


16. **Command: `curl`**
    - Description: Transfer data with URLs, which is useful for interacting with AWS APIs.
    - Usage: `curl -X <HTTP_METHOD> <API_URL> -H "Authorization`<br>
    

17. **Command: `wget`**
    - Description: Download files from the web, which can be useful for fetching data or scripts.
    - Usage: `wget <url>`<br>
      ![16,17](https://github.com/BhuvanesWaran00/AWS/assets/117109051/c49b73cf-331f-464d-838f-e46cc332c59d)


18. **Command: `mv`**
    - Description: Move files/directories.
    - Usage: `mv <source> <destination>`<br>
      ![18 mv](https://github.com/BhuvanesWaran00/AWS/assets/117109051/ca1ad6d3-3f4d-4de1-b721-c85776eb359e)

19. **Command: `chmod`**
    - Description: Change file permissions.
    - Usage: `chmod <permissions> <file>`<br>
    

20. **Command: `chown`**
    - Description: Change file ownership.
    - Usage: `chown <user>`<br>
      ![19,20 ](https://github.com/BhuvanesWaran00/AWS/assets/117109051/03902315-fd27-4054-96af-88232e7c48e9)


21. **Command: `ssh`**
    - Description: Securely connect to your AWS instances using SSH (Secure Shell) protocol.
    - Usage: `ssh -i <key_file> <username>@<instance_ip>`<br>
      ![21 ssh 1](https://github.com/BhuvanesWaran00/AWS/assets/117109051/3f46801c-5583-43e9-8055-677b37b7d3e1)
    - First time it asks permission but not work try again<br>
      ![21 ssh 2](https://github.com/BhuvanesWaran00/AWS/assets/117109051/ad1dee44-8d8a-40a1-a73c-5e90b74b8e5a)

22. **Command: `scp`**
    - Description: Securely copy files between local and remote systems.
    - Usage: `scp -i <key_file> <local_file> <username>@<instance_ip>`<br>
      ![22 scp](https://github.com/BhuvanesWaran00/AWS/assets/117109051/500eee07-620f-4096-b933-8ddc3fc3bbbd)


23. **Command: `rsync`**
    - Description: Efficiently synchronize files and directories between local and remote systems.
    - Usage: `rsync -avz -e "ssh -i <key_file>" <local_dir> <username>@<instance_ip>"`<br>
      ![23 rsync](https://github.com/BhuvanesWaran00/AWS/assets/117109051/3e7c8b87-1452-49b2-9911-af94f3d4027f)


24. **Command: `aws`**
    - Description: The AWS Command Line Interface (CLI) is used to interact with various AWS services from the command line.
    - Usage: `aws <service> <command> [options]`<br>
      ![24 aws](https://github.com/BhuvanesWaran00/AWS/assets/117109051/24870968-3a28-488d-9625-3bb4dd472749)


25. **Command: `top`**
    - Description: Monitor system performance and view resource usage in real-time.
    - Usage: `top`<br>
      ![25 top](https://github.com/BhuvanesWaran00/AWS/assets/117109051/9316549f-f602-4439-80d7-42dff42c2363)

26. **Command: `install`**
    - Description: Install new packege or application.
    - Usage: `<packege=i.e. (yum || apt-get)> install <applecation_name>`<br>
      ![26 install](https://github.com/BhuvanesWaran00/AWS/assets/117109051/28c8d79e-2785-451a-b828-dcdc96c69b2a)


27. **Command: `htop`**
    - Description: Interactive process viewer, an alternative to top.
    - Usage: `htop`<br>
      ![27 htop](https://github.com/BhuvanesWaran00/AWS/assets/117109051/4063c894-72aa-4c19-9495-8c5c72b90a14)


28. **Command: `grep`**
    - Description: Search for patterns in files or command output.
    - Usage: `grep "<pattern>" <file>`<br>
      ![28 grep](https://github.com/BhuvanesWaran00/AWS/assets/117109051/cc728e78-0b53-4962-88b7-07b0edd24884)


29. **Command: `tail`**
    - Description: Display the last few lines of a file (useful for log files).
    - Usage: `tail -n <num_lines> <file>`<br>
      ![29 tail](https://github.com/BhuvanesWaran00/AWS/assets/117109051/89de298d-f9c6-4a5c-90e1-c36fd3dfd2e4)



30. **Command: `history`**
    - Description: list all command fron login.
    - Usage: `history`<br>
      ![30 history](https://github.com/BhuvanesWaran00/AWS/assets/117109051/bd9fa0eb-7dae-4a08-8d00-4b87a7f9f930)
