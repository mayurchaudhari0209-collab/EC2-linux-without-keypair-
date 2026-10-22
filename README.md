# 🚀 Launch a Linux EC2 Instance on AWS Without a Key Pair

## 📌 Project Overview

This project demonstrates how to launch and access a Linux EC2 instance on Amazon Web Services (AWS) **without creating or downloading an SSH key pair**.

The project focuses on launching an EC2 instance, configuring network security, and connecting to the Linux server using AWS-supported access methods.

## 🎯 Project Objectives

- Launch a Linux EC2 instance without an SSH key pair.
- Configure security groups and network settings.
- Access the instance using AWS Systems Manager Session Manager.
- Execute basic Linux commands.
- Install and configure a web server.
- Understand secure EC2 access without managing SSH private keys.

## 🛠️ AWS Services and Tools

- **Amazon EC2** – Virtual Linux server
- **AWS Systems Manager (SSM)** – Secure instance access
- **AWS IAM** – Permissions and access management
- **Amazon VPC** – Networking infrastructure
- **Security Groups** – Network traffic control
- **Apache HTTP Server / Nginx** – Web server
- **Linux** – Operating system

## 🏗️ Project Architecture

User → AWS Management Console → Amazon EC2 Instance → Systems Manager Session Manager → Linux Terminal

## ⚙️ Implementation Steps

### Step 1: Launch an EC2 Instance

1. Sign in to the AWS Management Console.
2. Open the Amazon EC2 dashboard.
3. Select **Launch Instance**.
4. Enter an instance name, such as `Linux-Server`.
5. Select Amazon Linux 2023.
6. Choose an eligible instance type, such as `t3.micro`.
7. Under Key pair, select **Proceed without a key pair**.
8. Configure the network and security group.
9. Launch the instance.

### Step 2: Configure IAM Permissions

For Session Manager access:

1. Open the IAM console.
2. Create or select an appropriate EC2 IAM role.
3. Attach the `AmazonSSMManagedInstanceCore` policy.
4. Assign the role to your EC2 instance.

Use least-privilege permissions and follow your organization's security policies.

### Step 3: Connect to the Linux Instance

1. Open the EC2 console.
2. Select your running instance.
3. Choose **Connect**.
4. Open the **Session Manager** tab.
5. Click **Connect**.

The instance must have a functioning SSM Agent, the required IAM permissions, and network connectivity to Systems Manager endpoints.

### Step 4: Run Linux Commands

Check the operating system:

```bash
cat /etc/os-release
```

Check the current user:

```bash
whoami
```

Check disk usage:

```bash
df -h
```

Check memory:

```bash
free -h
```

Update installed packages:

```bash
sudo dnf update -y
```

### Step 5: Install Apache Web Server

Install Apache:

```bash
sudo dnf install httpd -y
```

Start Apache:

```bash
sudo systemctl start httpd
```

Enable Apache at boot:

```bash
sudo systemctl enable httpd
```

Check the service status:

```bash
sudo systemctl status httpd
```

Create a sample web page:

```bash
echo "<h1>Welcome to My AWS Linux Server</h1>" | sudo tee /var/www/html/index.html
```

### Step 6: Configure Web Access

1. Open the EC2 security group.
2. Add an inbound rule for HTTP.
3. Set the port to `80`.
4. Restrict the source to the appropriate trusted IP ranges or network.
5. Open the instance's public IPv4 address in a browser, if the instance has one.

Example:

```text
http://YOUR-EC2-PUBLIC-IP
```

Replace `YOUR-EC2-PUBLIC-IP` with your actual public IPv4 address.

## 🔐 Security Best Practices

- Avoid opening SSH port 22 to the entire internet.
- Use Systems Manager Session Manager instead of distributing private keys.
- Attach only the IAM permissions required by the instance.
- Restrict inbound HTTP and HTTPS traffic as appropriate.
- Use private subnets and Systems Manager VPC endpoints where suitable.
- Stop or terminate unused EC2 instances to help control costs.

**Important:** Launching an instance without a key pair does not automatically enable secure access. Configure and verify Systems Manager before relying on it.

## 📚 What I Learned

- Launching Amazon EC2 instances without SSH key pairs
- Configuring IAM roles and permissions
- Accessing Linux through Session Manager
- Executing essential Linux commands
- Installing and managing Apache
- Configuring security groups and web access
- Applying AWS security best practices

## 👨‍💻 Author

**Mayur Chaudhari**

B.Sc. Computer Science Graduate | DevOps with AWS Trainee

GitHub: [mayurchaudhari0209-collab](https://github.com/mayurchaudhari0209-collab)

Portfolio: [Visit My Portfolio](https://mayurchaudhari0209-collab.github.io/mayur-portfilo/)

---

⭐ If you find this project useful, feel free to explore the repository and share your feedback.

#AWS #AmazonEC2 #Linux #AWSSystemsManager #IAM #CloudComputing #DevOps
