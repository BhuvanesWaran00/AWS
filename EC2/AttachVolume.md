#  Attach Multiple Elastic Block Store (EBS) Volume in EC2 Instance
  - You can attach multiple EBS volumes to a single instance. The volume and instance must be in the same Availability Zone.
  - Depending on the volume and instance types, you can use Multi-Attach to mount a volume to multiple instances at the same time.    

## Prerequisites

Before you begin, ensure you have the following:

- An Amazon Web Services (AWS) account.
- An Amazon EC2 instance launched and running.
- The private key (.ppk) file associated with your EC2 instance.
- A terminal or SSH client installed on your local machine.

## Steps For Attach Volume
### Create & Attach a New volume with Amazon EC2 Instance
- Goto Ec2 Dashboard and click Volumes on the left sidebar
- Click Create Volume
- Enter volume type, size, availability zone
- Ensure Volume and Instances in same availability zone
  ![01 create volume](https://github.com/BhuvanesWaran00/AWS/assets/117109051/3aeb3bb2-b6d8-44ea-ada3-8ca3bb2b9810)

### Attach Volume with Instance
- After Volume creation see the volume state it shows: Available
- Select the volume
- And In actions select Attach Volume
- Select Instance
- Click Attach Volume
- Now see volume state it shows: In-use

  ![Screenshot 2023-09-14 131047](https://github.com/Bhuvanesan00/AWS/assets/117109051/81b6c59b-4e2b-4d27-b5a1-2c413e33a641)

### Format and mount an attached volume in Linux
- Log in to your instance in the terminal

   **lsblk**
    - Description: The lsblk command to view your available disk devices and their mount points (if applicable) to help you determine the correct device name to use.
    - Usage: `lsblk`
    - IMG 1: without new volume
      
      ![Screenshot 2023-09-14 193841](https://github.com/BhuvanesWaran00/AWS/assets/117109051/c8df36af-e1da-42b1-a3af-1687e9a10128)
    
    - IMG 2: with new volume
      
      ![lsblk](https://github.com/BhuvanesWaran00/AWS/assets/117109051/83a3f95a-ec8f-447f-a54f-5939ef6e7b00)
      
  **file -s**
    - Description:
        - file -s command to get information about a specific device, such as its file system type.
        - If the output shows simple data, as in the following example output, there is no file system on the device
    - Usage: `file -s /dev/<FileSystemName>`
    - IMG 1: already booted file system<br>
    
      ![Screenshot 2023-09-14 140236](https://github.com/BhuvanesWaran00/AWS/assets/117109051/7443c196-bdf4-40dc-951b-0f746f05d02d)
      
    - IMG 2: newly added file system file system|volume<br>
    
      ![Screenshot 2023-09-14 140540](https://github.com/BhuvanesWaran00/AWS/assets/117109051/213ebe81-b914-4151-84db-b0584afcc1e8)
      
  **lsblk -f**
    - Description: get information about all of the devices attached to the instance
    - Usage: `lsblk -f`
      
      ![Screenshot 2023-09-14 141254](https://github.com/BhuvanesWaran00/AWS/assets/117109051/81aadd8e-cbdd-4588-a2e5-98eda8cff57e)
  
  **mkfs -t**
    - Description:  Create a file system on the volume.
      - **Warning:** Do not use this command if you're mounting a volume that already has data on it 
    - Usage:
      - `mkfs -t xfs /dev/xvdf` || `mkfs -t ext4 /dev/xvdf`

        ![Screenshot 2023-09-14 194026](https://github.com/BhuvanesWaran00/AWS/assets/117109051/16a2368d-953d-4588-84dd-2ce751f97e44)

      
  **mkdir**
    - Description: Create a directory
    - Usage: `mkdir <DirName>`
      
      ![Screenshot 2023-09-14 142354](https://github.com/BhuvanesWaran00/AWS/assets/117109051/2652520a-71ae-4f2b-ab92-3273a89478a7)
  
  **mount**
    - Description: Mount the volume or partition at the mount point directory you created in the previous step.
    - Usage: `mount /dev/xvdf /<DirName>`
      
       ![Screenshot 2023-09-14 143404](https://github.com/BhuvanesWaran00/AWS/assets/117109051/dc3d639a-908d-4442-be9b-a76e3e129fe7)
      
- Now You can store any file in that directory  It will be stored in a new volume

  ![Screenshot 2023-09-14 200821](https://github.com/BhuvanesWaran00/AWS/assets/117109051/2bb43436-ad53-4481-a9c2-2eeb357ddcc3)
  

 ## Unmount and detach volume in Linux
 
 - Unmount
  - Description: unmount the volume or partition at the mount point directory.
  - Usage: `umount /dev/xvdf`
    
    ![Screenshot 2023-09-14 201022](https://github.com/BhuvanesWaran00/AWS/assets/117109051/5b034221-5df5-47fb-9387-5bdd29776251)

- detach Volume
  - Select the volume
  - And In actions select Detach Volume
  - now Volume state change available

## Attach volume with different Instance

After attaching volume with instance Follow the Below commands
```
# lsblk -f
# mkdir dir
# mount /dev/xvdf dir/
```


![Screenshot 2023-09-14 200106](https://github.com/BhuvanesWaran00/AWS/assets/117109051/5663eda4-e3ad-47c0-9020-80e2320dde88)


## Enable multi-attached Volume
- Volume --> create Volumes
- in Volume type Select Provisioned IOPS SSD (io1 || io2)
- in Amazon EBS Multi-Attach --> Enable Multi-Attach

  ![Screenshot 2023-09-16 120032](https://github.com/BhuvanesWaran00/AWS/assets/117109051/0ab06753-c24d-4306-a855-6e206f7beea6)

- **Warning:** If you're using a free-tier account you are not able to attach with t2.micro instance type

  ![Screenshot 2023-09-16 120305](https://github.com/BhuvanesWaran00/AWS/assets/117109051/29104f48-dabe-402a-9bf9-bbd80d1a8d45)
  
