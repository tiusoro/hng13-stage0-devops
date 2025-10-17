
````markdown
# 🚀 Deploy an NGINX Web Server on AWS

## 🎉 Welcome to My First DevOps Challenge!

This project demonstrates my ability to **deploy a web server** and **manage a GitHub workflow**, closely mirroring real-world DevOps environments.

---

## 🧩 Objectives

By the end of this task, I achieved the following:
- ✅ Set up and managed a GitHub repository.
- ✅ Deployed and configured an **NGINX** web server on **AWS EC2**.
- ✅ Served a **custom webpage** accessible from the internet.
- ✅ Built a **custom VPC network** from scratch.

---

## ⚙️ Part 1: GitHub Setup

**Steps:**
1. Forked the repository: `hng13-stage0-devops`
2. Added a `README.md` file containing:
   - My **Name**
   - My **Slack Username**
   - A **Short Project Description**

---

## ☁️ Part 2: NGINX Web Server Deployment

### 🧭 Infrastructure Overview

I built a custom AWS network architecture consisting of:

| Resource | Description |
|-----------|--------------|
| **VPC** | CIDR Block `10.0.0.0/16` |
| **Subnets** | Two Public Subnets for availability |
| **Internet Gateway (IGW)** | Enables internet access |
| **Route Table** | Routes outbound traffic (0.0.0.0/0) to the IGW |
| **Security Group** | Allows HTTP (80) and SSH (22) |
| **EC2 Instance** | Ubuntu instance running NGINX |

---

### 🔧 Step-by-Step Deployment

#### 1️⃣ Create a Custom VPC
```bash
VPC CIDR: 10.0.0.0/16
````

#### 2️⃣ Create Two Public Subnets

| Subnet Name     | Availability Zone | CIDR Block  |
| --------------- | ----------------- | ----------- |
| public-subnet-1 | us-east-1a        | 10.0.1.0/24 |
| public-subnet-2 | us-east-1b        | 10.0.2.0/24 |

✅ Enabled *auto-assign public IPv4* for both.

#### 3️⃣ Create and Attach an Internet Gateway

* Create and Attached IGW to the custom VPC.
created hng-igw and attached it to custom vpc hng-vpc

#### 4️⃣ Configure Route Table

* Destination: `0.0.0.0/0`
* Subnets Associations: public-subnet-1
                        public-subnet-2
* Edit Route then Add route 0.0.0.0/0 to internet gateway hng-igw.

#### 5️⃣ Create Security Group

Inbound Rules:

| Type | Port | Source    |
| ---- | ---- | --------- |
| HTTP | 80   | 0.0.0.0/0 |
| SSH  | 22   | 0.0.0.0/0 |

---

### 💻 Launch the EC2 Instance

* **AMI:** Ubuntu (latest)
* **VPC:** Custom VPC
* **Subnet:** public-subnet-1
* **Auto-assign Public IP:** Enabled
* **Security Group:** Custom SG (HTTP + SSH)

---

### 🌐 Install and Configure NGINX

```bash
sudo apt update -y
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
sudo systemctl status nginx
```
If successful, you’ll see your **custom NGINX web page**.
---

### 📝 Edit Web Page Content

```bash
sudo vi /var/www/html/index.html
```

Updated with the content from the forked project, as instructed.

---

### ✅ Testing the Deployment

Access the server in your browser using:

```
http://<your-ec2-public-ip>
e.g. http://54.205.143.172/

```

---

## 📊 Project Summary

| Component        | Purpose                           |
| ---------------- | --------------------------------- |
| GitHub Repo      | Version control and documentation |
| AWS VPC          | Custom isolated network           |
| Subnets          | Public access for web traffic     |
| Internet Gateway | Enables outbound internet         |
| EC2 Instance     | Hosts NGINX web server            |
| NGINX            | Serves static web page            |
| Security Group   | Firewall for SSH and HTTP         |

---

## 🧠 Key Learnings

* Hands-on experience with AWS networking fundamentals.
* Understanding of NGINX web server configuration.
* Version control and documentation with GitHub.
* How to connect infrastructure components for a production-ready setup.

---

## 👤 Author Information

* **Name:** Anthony Usoro
* **Slack Username:** @anthonyusoro
* **Project:** Deploy an NGINX Web Server on AWS

```

