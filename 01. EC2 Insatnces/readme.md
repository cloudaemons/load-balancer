# EC2 Instances

## DEFINITIONS
----

### EC2 Instance

An EC2 instance is a virtual server in Amazon's Elastic Compute Cloud (EC2) service which allows running different applications 

## STEPS
---

1. CREATE KEY PAIRS WHICH ALLOW TO ACCESS EC2 VIA SSH

    * Go to **EC2** section in the AWS console
    * Click **Key Pairs** in the left-hand menu
    * Click **Create Key Pair**
    * Name the key **myKey**
    * Click **Create**. It should generate **myKey.pem**. Save this file on your local computer
     
2. LAUNCH EC2 INSATNCE IN THE PUBLIC SUBNET ONE
    
    * Go to **EC2** section in the AWS console
    * Click **Launch Insstance**
    * Choose **Amazon Linux 2 AMI (HVM), SSD Volume Type** then click **Select**
    * Select **t2.micro** as an instance type
    * Click **Configure Instance Details**
    * Select previously created VPC, in the field **Network**
    * Select **publicOne** in the field **Subnet**
    * In section **Advenced Datails**, add code listed below in the field **User data**
    
    ```bash
    #!/bin/bash
    sudo yum install -y httpd
    sudo yum install -y wget
    cd /var/www/html
    sudo wget https://cloudaemons-workshop.s3-eu-west-1.amazonaws.com/web1/index.html
    sudo service httpd start
    ```
    
    * Click **Next: Add Storage** button
    * You can modify here the size of disk attached to your instance
    * Click **Next: Add Tags**
    * Go to security group section by clicking **Next: Configure Security Group**
    * Select an existing security group
    * Choose **mySgWeb** security group
    * Click **Review and launch**
    * Click **Launch**
    * Choose an existing key pair previously created
    * Acknowledge that you have access to the selected private key file
    * Click **Launch Instance** then **View instances**


3. LAUNCH EC2 INSATNCE IN THE PUBLIC SUBNET TWO

    * Go to **EC2** section in the AWS console
    * Click **Launch Instance**
    * Choose **Amazon Linux 2 AMI (HVM), SSD Volume Type** then click **Select**
    * Select **t2.micro** as an instance type
    * Click **Configure Instance Details**
    * Select previously created VPC, in the field **Network**
    * Select **publicTwo** in the field **Subnet**
    * In section **Advenced Datails**, add code listed below in the field **User data**
    
    ```bash
    #!/bin/bash
    sudo yum install -y httpd
    sudo yum install -y wget
    cd /var/www/html
    sudo wget https://cloudaemons-workshop.s3-eu-west-1.amazonaws.com/web2/index.html
    sudo service httpd start
    ```
    
    * Click **Next: Add Storage** button
    * You can modify here the size of disk attached to your instance
    * Click **Next: Add Tags**
    * Go to security group section by clicking **Next: Configure Security Group**
    * Select an existing security group
    * Choose **mySgWeb** security group
    * Click **Review and launch**
    * Click **Launch**
    * Choose an existing key pair previously created
    * Acknowledge that you have access to the selected private key file
    * Click **Launch Instance** then **View instances**
    


## END OF LAB

You have created ec2 instances, now you can go to the next part of this lab
