# EC2 & CloudWatch & SNS
> Create Ec2 Instance & Install Apache using UserData
> Create an alarm for CPU Utilization with SNS topic and subscription
> Host a Website

## Create Ec2 Instance & Install Apache using UserData
+ Lanch Ec2 Instance with configuration Which you want
+ In `Advanced details --> User data` Use the below script
```bash script
#! /bin/bash
yum install httpd -y
service httpd start
```
![User_Data](https://github.com/BhuvanesWaran00/AWS/assets/117109051/1e4ddc01-d812-4ddf-9ff3-596fe73e61b3)
+ Launch Instance
## Create an alarm for Memory & Disk with SNS topic and subscription
+ Goto `CloudWatch --> Create alarm`
    + `Select metric --> EC2 --> Per-Instance Metrics` 
    + Select your instance_id & CPU Utilization
    + ![CW](https://github.com/BhuvanesWaran00/AWS/assets/117109051/2605762e-80e9-453c-9192-efb6340c1519)
    + ![cw](https://github.com/BhuvanesWaran00/AWS/assets/117109051/7ae29632-f658-4219-b7a4-8955e3ffc467)
    + next
    + In Notification `Create new topic --> mention your e-mail --> Create Topic`
    + ![Screenshot 2023-08-10 132252](https://github.com/BhuvanesWaran00/AWS/assets/117109051/38a7f51a-d69e-4998-bedc-ab9154ad541a)
    + then mention `Name and description`
    + Create Alarm
    + You got a mail from AWS For Conformation `Just Click confirm Subscripton`
    + now host your website \( It will make a changes your CPU utilization )
    + Now you get an Alert e-mail
    + ![Screenshot_20230810_140851](https://github.com/BhuvanesWaran00/AWS/assets/117109051/8699d301-17db-46d6-9da6-f0c808f49165)

