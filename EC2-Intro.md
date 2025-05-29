📘 Amazon EC2 (Elastic Compute Cloud) -

🧠 Introduction

Amazon EC2 (Elastic Compute Cloud) is a web service provided by AWS that allows users to run virtual servers in the cloud. These virtual servers, known as instances, provide resizable compute capacity and are a key part of scalable and flexible cloud infrastructure.


---

🎯 Core Concepts

Concept	Description

AMI (Amazon Machine Image)	A pre-configured OS image used to launch EC2 instances.
Instance Type	Defines the hardware (CPU, memory, storage, network) of the EC2. E.g., t2.micro, m5.large.
Key Pair	Used for SSH access to the instance. Public key is stored by AWS; private key is downloaded by user.
Security Groups	Virtual firewall to control inbound and outbound traffic to your instances.
Elastic IP	A static, public IPv4 address that can be attached to an EC2 instance.
EBS (Elastic Block Store)	Persistent block storage that can be attached to EC2 instances.



---

🚀 Launching an EC2 Instance (Theory + Steps)

✅ Step-by-Step Process

1. Login to AWS Console


2. Go to EC2 Dashboard


3. Click on Launch Instance


4. Configure:

Name and tags

AMI (choose Amazon Linux 2 or Ubuntu)

Instance type (e.g., t2.micro)

Key pair (create new or use existing)

Network settings (select/create VPC and Security Group)

Storage (default is 8 GiB EBS)



5. Click Launch



🔐 Accessing Your Instance

chmod 400 your-key.pem
ssh -i "your-key.pem" ec2-user@<public-ip>


---

🛡️ Security Group Configuration (Example)

Type	Protocol	Port Range	Source

SSH	TCP	22	Your IP
HTTP	TCP	80	0.0.0.0/0
HTTPS	TCP	443	0.0.0.0/0



---

💼 Real-World Use Cases

Hosting a web server (Apache/Nginx)

Deploying a database (MySQL/PostgreSQL)

Running backend APIs (Node.js, Django, Flask)

Setting up a bastion server for secure access

Launching a containerized app (via Docker or ECS)



---

⚙️ Common EC2 Solutions

1. Install Apache Web Server

sudo yum update -y           # For Amazon Linux
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd

2. Attach an EBS Volume

# View disk
lsblk

# Create file system
sudo mkfs -t xfs /dev/xvdf

# Mount
sudo mkdir /mnt/data
sudo mount /dev/xvdf /mnt/data

# Persistent mount
echo "/dev/xvdf /mnt/data xfs defaults,nofail 0 2" | sudo tee -a /etc/fstab

3. Update the EC2 Hostname

sudo hostnamectl set-hostname my-ec2-server


---

📦 Best Practices

Use IAM roles to assign permissions instead of storing credentials.

Keep ports closed unless required (SSH on 22 should be limited to your IP).

Regularly backup EBS volumes using snapshots.

Enable CloudWatch monitoring for usage metrics.

Use Auto Scaling Groups for high availability and load handling.

Schedule stop/start to save costs during idle hours.



---

🧪 Hands-on Projects

🔧 Deploy a LAMP stack (Linux, Apache, MySQL, PHP)

🐳 Host a Docker container

🔄 Configure EC2 with an Elastic Load Balancer and Auto Scaling

🌐 Create a simple website hosted on EC2 and mapped to a domain via Route 53



---

📚 Resources

AWS EC2 Documentation

EC2 Instance Pricing

Amazon Linux 2 AMI Guide



---

✅ Checklist Before Terminating

Backup data from EBS or instance storage

Unassign and release Elastic IP if not needed

Terminate the instance properly to avoid extra charges



---

👨 💻 Author

Shaikh Ahsan
Learning AWS Cloud, EC2, and DevOps Tools

