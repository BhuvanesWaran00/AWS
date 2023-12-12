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
- tag: master
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
  - in this creates new VPC, Subnets, RT, IGW, NATGW, ASG by default
  ```
  # create cluster
  eksctl create cluster --version=1.27 --name=cluster --nodes=1 --managed --region=<region_code> --zones <AZ1>,<AZ2> --node-type t2.micro --asg-access
  # create nodegroup
  eksctl create nodegroup --cluster=cluster --managed --region=<region_code> --spot --name=spot-node-group-2vcpu-8gb --instance-types=t2.small,t2.micro,t2.medium --nodes-min=1 --nodes-max=1 --asg-access
  ```
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/bc742a11-d86a-4da6-a74c-18f376572040)
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/793230fc-be67-45e6-9521-31c5ce9fc30d)
  ![Screenshot 2023-12-12 104825](https://github.com/BhuvanesWaran00/AWS/assets/117109051/1b7a3b80-e102-46da-a20b-a897e578f705)
- after this step select the master instance
  - Actions --> Image and Templates --> Launch more like this
  - Select VPC:**eksctl-cluster-cluster/VPC** and **public subnet**
  - Terminate old Instance
- login Instance
- view web files at `cd /app` `ls`
  ![Web Files](https://github.com/BhuvanesWaran00/AWS/assets/117109051/12239974-0feb-43c6-8973-e96ea64d6c4d)
- For server identification `cd templates/` `vi registration.html`<br>
  change your region name || If you don't want to delete that line
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/8fa68b00-d1d1-4a8a-90af-ad371eab7341)
- cluster config with kubernetes
  ```
  aws configure
  # enter Access Key ID
  # enter Secret Access Key
  # enter region name
  # enter output format
  
  aws eks update-kubeconfig --region <region_code> --name <cluster_name>

  # Test your configuration, with the following command:
  kubectl get svc
  ```
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/24b63d5e-893a-40d1-abab-eef55bdd126e)

- **Do the same process on the secondary region also**

### RDS Setup
- RDS creates a database
- Engine options: MySQL
- Mention DB instance identifier, Master username, Master password
- Select  VPC:**eksctl-cluster-cluster/VPC**
  
  ![Screenshot 2023-12-12 110143](https://github.com/BhuvanesWaran00/AWS/assets/117109051/0ec6e2fc-dfb7-413f-be3c-094efaf6463f)

- RDS takes 5 - 10 mins for creation
- actions --> Set up EC2 connection (instance: master) --> continue --> setup
- log on to the instance master
- add environmental variables
  ```
  echo 'export DB_HOST="eks.cnwgdt8jxjvf.ap-northeast-2.rds.amazonaws.com"' >> ~/.bashrc
  echo 'export DB_USER="root"' >> ~/.bashrc
  echo 'export DB_PASSWORD="Bh101299"' >> ~/.bashrc
  echo 'export DB_NAME="userdata"' >> ~/.bashrc
  source ~/.bashrc
  ```
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/f79b3827-2a00-44ed-ad5d-9afb6cb81fdd)

- login MySQL
  ```
  mysql -h $DB_HOST -u $DB_USER -P 3306 -p
  # Enter Your Password
  ```
- create database
  ```sql
  Source database.sql
  exit
  ```
  
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/0603033c-e44b-4889-9a9d-3c61374a7bd7)

- add data to the table
  ```python
  pip install -r requirements.txt
  python3 insertLaptops.py
  ```
- configure Dockerfile `vi /app/Dockerfile` to replace RDS required data
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/41c819bd-f15e-47e4-8a6e-5a05f796f4b1)

- Action --> Create read replica --> Select DR region
### ECR Setup
  ```
  # create ECR Repo
  aws ecr create-repository --repository-name eks_dr_project --region <region_code>

  # docker login
  aws ecr get-login-password --region <your-region> | docker login --username AWS --password-stdin <your-account-id>.dkr.ecr.<your-region>.amazonaws.com

  # Build Docker image
  docker build -t eks_dr_project .

  # tag a image
  docker tag eks_dr_project:latest <your-account-id>.dkr.ecr.<your-region>.amazonaws.com/eks_dr_project:latest

  #  push the image to repository
  docker push <your-account-id>.dkr.ecr.<your-region>.amazonaws.com/eks_dr_project:latest
  ```
  ![image](https://github.com/BhuvanesWaran00/AWS/assets/117109051/0f3d86e5-9e21-4dcb-82a8-66fa09781d43)

- **Do the same process on the secondary region also**
