# DevOps Guide

## 📌 Project Summary

This repo provides a step-by-step guide for setting up a web app in the cloud as part of a **7-Day DevOps Challenge**:

- **Launch an EC2 Instance** on AWS.
- **Set up VSCode** for remote development.
- **Connect via SSH** to the EC2 instance.
- **Install Apache Maven & Amazon Corretto 8** for Java development.
- **Create a Java Web App** using Maven.
- **Set up Git & push code to GitHub**.

## 🚀 Quick Start

### 1️⃣ Launch EC2 Instance
1. Log in to AWS as IAM Admin.
2. Go to **EC2 > Launch Instances**.
3. Select **Amazon Linux 2023 AMI**, `t2.micro`.
4. Create **key pair** (`nextwork-keypair`), store `.pem` in `DevOps` folder.
5. Configure **network** (Allow SSH traffic from **My IP**).
6. Click **Launch Instance**.

### 2️⃣ Set Up VSCode
1. **Install VSCode**.
2. Open **Terminal**, navigate to `DevOps` folder.
3. Verify `.pem` file:
   ```sh
   ls  # Mac/Linux
   dir # Windows
   ```
4. Change permissions:
   ```sh
   chmod 400 nextwork-keypair.pem  # Mac/Linux
   ```

### 3️⃣ Connect to EC2 via SSH
1. Find **Public IPv4 DNS** in AWS EC2.
2. Connect:
   ```sh
   ssh -i ~/Desktop/DevOps/nextwork-keypair.pem ec2-user@[YOUR_PUBLIC_IPV4_DNS]
   ```

### 4️⃣ Install Java & Maven
```sh
wget https://archive.apache.org/dist/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.tar.gz
sudo tar -xzf apache-maven-3.5.2-bin.tar.gz -C /opt
sudo dnf install -y java-1.8.0-amazon-corretto-devel
```

### 5️⃣ Create Web App with Maven
```sh
mvn archetype:generate \
   -DgroupId=com.nextwork.app \
   -DartifactId=nextwork-web-project \
   -DarchetypeArtifactId=maven-archetype-webapp \
   -DinteractiveMode=false
```

### 6️⃣ Set Up Git & Push to GitHub
1. Install Git:
   ```sh
   sudo dnf install git -y
   ```
2. Initialize & push code:
   ```sh
   git init
   git add .
   git commit -m "Initial commit"
   git push -u origin master
   ```

## 🎉 Congratulations!
Your web app is now deployed in AWS! 🚀

