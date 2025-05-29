📘 EC2 Basics – In-depth Theory

1. 🌐 Instance Types

An EC2 Instance is a virtual server in Amazon's Elastic Compute Cloud (EC2) for running applications on the AWS infrastructure.

Instance Types define the hardware of the host computer used for your instance. Each type offers different compute, memory, storage, and networking capabilities.

Categories of Instance Types:

Category	   Description	                                        Use Case Examples
General Purpose	   Balanced compute, memory,and networking resources	Web servers, Dev/Test, small databases
Compute Optimized  High-performance processors	         High-performance web servers, batch processing
Memory Optimized   Designed for memory-intensive applications	Databases, in-memory caches
Storage Optimized  High, sequential read and write access to large data sets	Data warehousing, Hadoop
Accelerated Computing	Use hardware accelerators like GPUs	Machine learning, video processing


Examples:

t2.micro, t3.medium → General Purpose

c5.large, c6g.xlarge → Compute Optimized

r5.large, x1.16xlarge → Memory Optimized

i3.large, d2.8xlarge → Storage Optimized

p2.xlarge, g4ad.xlarge → GPU/Accelerated Computing



2. 🧱 AMI (Amazon Machine Image)

An AMI is a template that contains the software configuration (OS, application server, and applications) required to launch an instance.

An AMI includes:

A root volume snapshot (e.g., OS like Ubuntu, Windows, etc.)

Launch permissions (who can launch instances)

Block device mapping (data volumes)

Types of AMIs:

AWS-provided AMIs (e.g., Amazon Linux 2, Ubuntu, Windows)

Marketplace AMIs (paid or free)

Custom AMIs (you create them with specific configurations)

Why AMIs Matter:

Helps launch instances with predefined configurations

Speeds up infrastructure deployments

Ensures consistency across instances

Creating a Custom AMI:

Launch and configure an EC2 instance.

Create an image (AMI) from the instance.

Use that AMI to launch identical instances later.

3. 🔐 Key Pairs
Definition:
A Key Pair is a set of security credentials (private key + public key) used to securely access EC2 instances.

AWS stores the public key.

You download the private key (.pem file) when you create the key pair.

Use:
Used for SSH (Secure Shell) access to Linux instances or RDP (Remote Desktop) to Windows instances.

Important Points:

You can’t download the .pem file again after creation. Keep it safe!

Use chmod 400 key.pem to secure your private key on Linux.

Without a key pair, you can't connect to your instance unless another method (e.g., SSM) is enabled.

Creating a Key Pair:

Go to EC2 Dashboard → Key Pairs → Create key pair

Choose RSA or ED25519 type

Download the .pem file and use it to SSH:

bash

ssh -i "your-key.pem" ec2-user@your-ec2-ip


4. 📝 User Data

User Data is a feature that allows you to automate tasks at the time of EC2 instance launch.

You can provide a shell script (Linux) or PowerShell script (Windows) that runs automatically once when the instance launches.

Use Cases:

Install software (e.g., Apache, NGINX)

Configure settings

Run initialization scripts

Example (Linux - Install Apache):

bash

#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "Welcome to EC2 Instance" > /var/www/html/index.html

Where to Add User Data:

.While launching the instance → Advanced Details → User Data
