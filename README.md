# SETTING UP A SCALABLE FILE STORAGE SYSTEM USING AMAZON ELASTIC FILE SYSTEM
## AIM
   To  setting up a scalable file storage system using Amazon Elastic File System (EFS) for two EC2 instances in different availability zones. 
## PROBLEM STATEMENT
   This experiment demonstrates how to configure Amazon EFS to provide a shared storage solution for two Linux EC2 instances across different availability zones, enabling easy data sharing. The aim is to ensure both instances can mount and access the EFS file system and validate data consistency across instances.

## ALGORITHM

### Steps 1: Create two EC2 instances in different availability zones.
Go to the EC2 service in the AWS Management Console.

Launch two Linux-based EC2 instances (e.g., Amazon Linux 2) and place them in different availability zones within the same VPC.

Assign each instance a security group that allows NFS access on port 2049.

### Steps 2: Set up a security group that allows necessary communication between the instances and EFS.
Create or configure a security group that allows inbound NFS traffic on port 2049 from the security group of both EC2 instances.

Attach this security group to the EFS file system to permit access from both instances.

### Steps 3: Create an EFS file system and mount it to both EC2 instances.
In the AWS Console, navigate to the EFS service and select Create file system.

Select the same VPC as your EC2 instances and configure mount targets in the availability zones where your instances are located.

Complete the setup and take note of the file system ID (e.g., fs-064645ac116a12816).
 
 ### Steps 4: Ensure that the EC2 instances can access the file system and share data between them.

## COMMANDS

## EC2 Instance 1
```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
vi file  # Create a file and add some text
```


EC2 Instance 2
```
sudo su
yum install httpd -y
yum install -y amazon-efs-utils
mount -t efs -o tls fs-064645ac116a12816:/ /var/www/html
cd /var/www/html
ls
cat file  
```

## OUTPUT

### REG NUMBER:212222230182 
### NAME:YUVARAJ B

## Creation two EC2 instances in different availability zones:

![WhatsApp Image 2024-09-19 at 11 13 47_31b2adf6](https://github.com/user-attachments/assets/775914d6-8fff-49f6-b93b-8d6ab74930d4)

## Set up of a security group that allows necessary communication between the instances and EFS:

![WhatsApp Image 2024-09-19 at 10 49 28_4111682a](https://github.com/user-attachments/assets/c569f982-f26f-4055-9827-5e964d5c1fb4)

## Set up of a security group that allows necessary communication between the instances and EFS:

## OUTPUT AT INSTANCE 1:
![WhatsApp Image 2024-09-19 at 10 49 28_09d6090b](https://github.com/user-attachments/assets/14468364-6990-48ad-96f2-bced646e3a8f)

## OUTPUT AT INSTANCE 2:
![WhatsApp Image 2024-09-19 at 10 49 28_714e0979](https://github.com/user-attachments/assets/92cbbbc6-c103-4272-8fc5-ecaa49c48c7b)

 
## RESULT
 
Successfully set up a scalable file storage system using Amazon EFS shared between two Linux EC2 instances in different availability zones, enabling consistent data sharing.
  


