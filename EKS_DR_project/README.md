# EKS Disaster Recovery project
The EKS Disaster Recovery project ensures the continuity of Amazon EKS Kubernetes clusters by implementing a multi-region deployment strategy, backup and restore mechanisms, and automated failover procedures.
## Tools and Services Used
### AWS Services

**IAM:** AWS Identity and Access Management (IAM) is a service for managing user permissions and access to AWS resources securely.

**VPC:** Amazon Virtual Private Cloud (VPC) enables users to create isolated, customizable network environments within the AWS cloud.

**EC2:** Amazon Elastic Compute Cloud (EC2) provides scalable virtual servers in the cloud, allowing users to run applications with flexibility and control.

**EKS:** Amazon EKS (Elastic Kubernetes Service) simplifies containerized applications' deployment, management, and scaling using Kubernetes.

**ECR:** Amazon Elastic Container Registry (ECR) is a fully managed Docker container registry, making storing, managing, and deploying Docker container images easy.

**RDS:** Amazon Relational Database Service (RDS) offers managed relational databases, supporting various database engines for scalable and secure data storage.

**ELB & ASG:** Elastic Load Balancing (ELB) distributes incoming application traffic, and Auto Scaling Groups (ASG) automatically adjusts the number of EC2 instances based on demand.

**CloudFormation:** AWS CloudFormation allows users to define and deploy infrastructure as code, automating the creation and management of AWS resources.

**Route53:** Amazon Route 53 is a scalable and highly available Domain Name System (DNS) web service, that provides domain registration and routing capabilities.

### Tools

**Docker:** Docker is a platform for developing, shipping, and running container applications, promoting consistency across different environments.

**Python (Flask):** Flask is a lightweight web framework for Python, commonly used to build and deploy web applications.

**Kubernetes:** An open-source container orchestration platform, Kubernetes automates the deployment, scaling, and management of containerized applications.

**AWS CLI:** The AWS Command Line Interface (CLI) is a unified tool for managing AWS services, providing a streamlined interface for command-line interactions.

**MySQL:** A popular open-source relational database management system, MySQL is widely used for scalable and reliable data storage within AWS.

**Git&GitHub:** To manage and share source code repositories, track changes, and collaborate on projects with features like pull requests, issues, and actions.

## Steps-to-Setup
### EC2 Setup
- Launch instances
- AMI: Amazon Linux
- select Key pair
- Advanced details --> User data --> type below script
```
#!/bin/bash
yum update -y
yum install python3 mariadb105 pip git -y
mkdir app
cd app
git clone https://github.com/BhuvanesWaran00/AWS.git
mv AWS/EKS_DR_project/* .
rm -rf AWS/
chmod +x docker_install_AL.sh k8s_ins.sh
./docker_install_AL.sh
./k8s_ins.sh
```
- login Instance
- view web files at `cd /app` `ls`
  ![Web Files](https://github.com/BhuvanesWaran00/AWS/assets/117109051/12239974-0feb-43c6-8973-e96ea64d6c4d)
- For server identification `cd templates/` `vi registration.html`<br>
  change your region name || If you don't want to delete that line
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/8fa68b00-d1d1-4a8a-90af-ad371eab7341)
- AWS CLI Configuration || Prerequisite (IAM user access & secret keys with required Permissions)
  ```
  aws configure
  # enter Access Key ID
  # enter Secret Access Key
  # enter region name
  # enter output format
  ```
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/a2502d19-e114-4590-abff-74225be038fd)
- **EKS Cluster & Nodegroup setup**
  ```
  # create cluster
  eksctl create cluster --version=1.27 --name=cluster --nodes=1 --managed --region=<region_code> --zones <AZ1>,<AZ2> --node-type t2.micro --asg-access
  # create nodegroup
  eksctl create nodegroup --cluster=cluster --managed --region=<region_code> --spot --name=spot-node-group-2vcpu-8gb --instance-types=t2.small,t2.micro,t2.medium --nodes-min=1 --nodes-max=1 --asg-access
  ```
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/bc742a11-d86a-4da6-a74c-18f376572040)
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/793230fc-be67-45e6-9521-31c5ce9fc30d)

- **Do the same process on the secondary region also**




### RDS Setup
- RDS creates a database
- Engine options: MySQL
- 


