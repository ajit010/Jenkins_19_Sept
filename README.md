# Jenkins CI/CD Training Notes

> Comprehensive notes covering Jenkins fundamentals, CI/CD concepts, DevOps basics, AI prompting, AWS labs, and Jenkins installation.

---

# Table of Contents

- Introduction
- What is CI and CD?
- DevOps Overview
- Jenkins Overview
- History of Jenkins
- Key Features of Jenkins
- Cloud Service Models
- AI & Prompt Engineering Basics
- LLMs vs Foundation Models
- Context Window
- Hands-on Labs
- Useful Linux Commands

---

# Introduction

Jenkins is one of the most popular open-source automation servers used for implementing **Continuous Integration (CI)** and **Continuous Delivery/Deployment (CD)**.

During this training you will learn:

- Jenkins fundamentals
- Jenkins UI
- CI/CD Pipelines
- AWS Integration
- Git Integration
- Docker Integration
- Plugin Management
- DevOps Concepts
- Basic AI Prompt Engineering for DevOps

---

# Jenkins Fundamentals

Topics covered:

- Jenkins Installation
- Jenkins Dashboard
- Jobs
- Builds
- Source Code Management (SCM)
- Plugins
- Build History
- Pipeline
- Testing Integration
- Deployment Automation

---

# What is CI (Continuous Integration)?

Continuous Integration is the practice of automatically integrating code changes from multiple developers into a shared repository.

Typical developer workflow:

```
Developer
     ↓
Write Code
     ↓
Commit Code
     ↓
Push to Git Repository
     ↓
Pull Request
     ↓
Code Review
     ↓
Merge to Main Branch
     ↓
Automated Jenkins Pipeline
     ↓
Build
     ↓
Testing
```

### Example

A development team may commit code **20+ times a day**.

Instead of manually building and testing every change, Jenkins automatically:

- Detects the new commit
- Pulls latest code
- Builds the application
- Runs automated tests
- Reports success/failure

This is Continuous Integration.

---

# What is CD (Continuous Delivery / Continuous Deployment)?

Once CI is complete and all tests pass, the application is ready for deployment.

```
Source Code
      ↓
Build
      ↓
Testing
      ↓
Artifact Ready
      ↓
Deploy to Development
      ↓
Deploy to Staging
      ↓
Deploy to Production
```

There are two common CD approaches:

## Continuous Delivery

Deployment is automated **up to production**, but requires **human approval** before releasing.

```
Build
 ↓
Test
 ↓
Ready
 ↓
Manual Approval
 ↓
Production
```

---

## Continuous Deployment

Everything is automated.

```
Build
 ↓
Test
 ↓
Deploy
 ↓
Production
```

No manual intervention is required.

---

# DevOps Overview

DevOps is a culture that improves collaboration between Development and Operations teams.

Goals:

- Faster software delivery
- Early testing
- Fail fast
- Automated deployments
- Continuous monitoring

Popular DevOps tools:

- Git
- Jenkins
- Docker
- Kubernetes
- Terraform
- Ansible

---

# Jenkins in DevOps

Examples:

## AWS Automation

Write a Jenkins Pipeline that:

- Creates EC2 instances
- Configures them
- Destroys them automatically

```
Jenkins
      ↓
AWS Plugin
      ↓
EC2 Creation
```

---

## Docker Automation

Pipeline can:

- Build Docker Images
- Tag Images
- Push Images to Docker Hub

```
Git
 ↓
Jenkins
 ↓
Docker Build
 ↓
Docker Hub
```

---

# Jenkins Overview

Jenkins is:

- Open-source
- Written in Java
- Automation Server
- Extensible using plugins

Primary use cases:

- Continuous Integration
- Continuous Delivery
- Build Automation
- Testing Automation
- Deployment Automation

It automates software delivery in a reliable and repeatable manner.

---

# History of Jenkins

| Year | Event |
|-------|------|
| 2004 | Hudson created at Sun Microsystems |
| 2010 | Oracle acquired Sun Microsystems |
| 2011 | Hudson renamed to Jenkins |
| Today | One of the world's most popular CI/CD tools |

---

# Key Features of Jenkins

---

## 1. Pipeline Support

Pipelines define complete software workflows.

Typical stages:

```
Checkout
      ↓
Build
      ↓
Test
      ↓
Package
      ↓
Deploy
```

Pipeline code is stored inside a **Jenkinsfile**.

Language used:

- Groovy DSL (Domain Specific Language)

---

## 2. Plugin Ecosystem

Jenkins has thousands of plugins.

Examples:

- AWS
- Docker
- Kubernetes
- Terraform
- Git
- Maven
- SonarQube
- Slack

Plugins extend Jenkins functionality.

### Restaurant Analogy

```
Customer
    ↓
Waiter (Jenkins)
    ↓
Kitchen
    ↓
Chef (Plugin)
    ↓
Food (Output)
```

Example:

AWS Plugin performs AWS operations and returns logs to Jenkins.

---

## 3. Distributed Builds

Jenkins supports multiple build agents.

```
               Master Node
                   │
        ┌──────────┴──────────┐
        │                     │
   Worker Node 1        Worker Node 2
```

Benefits:

- Better scalability
- Faster builds
- Parallel execution

---

## 4. Source Code Integration

Jenkins integrates with:

- Git
- GitHub
- GitLab
- Bitbucket
- Mercurial
- Subversion

Authentication methods:

- Username & Password
- Personal Access Token (PAT)
- SSH Keys

Environment Variables example:

```bash
$DOCKERHUB_USERNAME
$AWS_ACCESS_KEY_ID
$AWS_SECRET_ACCESS_KEY
```

---

## 5. Build Triggers

### Time-based Trigger

Uses Cron expressions.

Examples:

- Every 5 minutes
- Every 2 hours
- Daily
- Weekly

---

### Webhook Trigger

Automatically starts a pipeline whenever code is pushed to GitHub.

```
GitHub Push
      ↓
Webhook
      ↓
Jenkins
      ↓
Pipeline
```

---

### SCM Polling

Jenkins checks the repository periodically.

Example:

Every 10 minutes.

---

## 6. RBAC (Role-Based Access Control)

Manage user permissions.

Examples:

- Administrator
- Developer
- Viewer
- Build Operator

---

# Cloud Service Models

---

## 1. Infrastructure as a Service (IaaS)

Provides maximum infrastructure control.

Examples:

- Amazon EC2
- Azure Virtual Machines
- Google Compute Engine

Users choose:

- Operating System
- CPU
- RAM
- SSD/HDD
- IOPS

Suitable for:

- System Administrators
- Infrastructure Teams

---

## 2. Platform as a Service (PaaS)

Developers focus on writing code.

Infrastructure is managed by the cloud provider.

Examples:

- AWS Elastic Beanstalk
- Amazon RDS
- Amazon Aurora

Databases:

- MySQL
- PostgreSQL

---

## 3. Function as a Service (FaaS)

Serverless computing.

Example:

AWS Lambda

Features:

- Auto Scaling
- Pay-per-use
- No server management

---

## 4. Software as a Service (SaaS)

Ready-to-use software over the internet.

Examples:

- ChatGPT
- Gmail
- Microsoft 365

---

# AI & Prompt Engineering

Modern DevOps engineers increasingly use AI tools such as:

- ChatGPT
- Claude
- Kiro
- GitHub Copilot

Example use case:

> "Create a Jenkins Pipeline that launches two EC2 instances in the us-east-1 region using t2.medium instances."

---

# Prompt Engineering Techniques

## Zero-shot Prompt

Ask directly.

Example:

> What is the capital of Italy?

---

## Few-shot Prompt

Provide examples before asking.

Example:

```
English → Spanish

Hello → Hola

Now translate:

Thank you
```

---

## Role-based Prompting

Assign a role to the AI.

Example:

```
You are a DevOps Engineer.

Create a Jenkins Pipeline
that launches two EC2 instances
in us-east-1 using t2.medium.
```

---

# LLM vs Foundation Models

## Large Language Model (LLM)

Designed primarily for text generation.

Examples:

- GPT
- Claude
- Llama

Characteristics:

- Natural Language Processing
- Billions of parameters
- Text generation

---

## Foundation Model (FM)

A broader category.

Can generate:

- Text
- Images
- Audio
- Video

LLMs are a subset of Foundation Models.

---

# Single-modal vs Multi-modal Models

## Single-modal

Input:

```
Text
```

Output:

```
Text
```

---

## Multi-modal

Accepts multiple input types.

Examples:

- Text
- Images

Produces:

- Text
- Images
- Code

---

# Popular AI Models

| Company | Models |
|----------|---------|
| OpenAI | GPT-5.5, GPT-5.1, GPT-4.1 |
| Anthropic | Claude Sonnet, Opus, Haiku |
| Meta | Llama |
| Amazon | Titan |

---

# Context Window

A context window is the amount of information an AI model can remember during a conversation.

Example:

```
Prompt 1
150 Tokens

↓

Response
2000 Tokens

↓

Prompt 2

↓

Entire conversation becomes context
```

Once the context limit is reached:

- Older information may be forgotten
- Start a new chat for a fresh context

---

# Hands-on Labs

---

# Lab 1 – Create an AWS Free Tier Account

## Objective

Create an AWS Free Tier account that will be used throughout the Jenkins CI/CD training.

## Prerequisites

- A valid email address
- A mobile phone number for verification
- A debit/credit card for identity verification (AWS may perform a temporary authorization; Free Tier eligible resources are available at no cost within limits.)

## Step 1: Visit AWS

Open your browser and navigate to:

```
https://aws.amazon.com/free/
```

Click **Create a Free Account**.

---

## Step 2: Create an AWS Account

Enter the following details:

- Email Address
- Password
- AWS Account Name

Example:

```
Email:
john.doe@gmail.com

AWS Account Name:
john-training
```

Click **Continue**.

---

## Step 3: Verify Email Address

AWS sends a verification code to your email.

- Open your mailbox.
- Copy the verification code.
- Enter it on the AWS registration page.

---

## Step 4: Create Root User Password

Choose a strong password that includes:

- Uppercase letters
- Lowercase letters
- Numbers
- Special characters

Example:

```
Example@123
```

> Store the password securely.

---

## Step 5: Contact Information

Select:

```
Personal Account
```

Fill in:

- Full Name
- Phone Number
- Country
- Address
- City
- State
- Postal Code

Accept the AWS Customer Agreement.

---

## Step 6: Billing Information

Enter your debit or credit card details.

AWS uses this information for identity verification.

> AWS Free Tier resources remain free as long as you stay within Free Tier limits.

---

## Step 7: Identity Verification

Complete phone verification.

AWS sends an OTP to your registered mobile number.

Enter the OTP.

---

## Step 8: Select Support Plan

Choose:

```
Basic Support (Free)
```

Click **Complete Sign Up**.

---

## Step 9: Login to AWS Console

Visit:

```
https://console.aws.amazon.com
```

Sign in using your Root User credentials.

You should now see the AWS Management Console.

---

## Lab Outcome

✅ AWS Account Created

✅ Successfully logged into AWS Console

---

# Lab 2 – Create an IAM User

## Objective

Create an IAM User with Administrator permissions instead of using the Root Account.

> **Best Practice:** Never perform day-to-day activities using the Root User.

---

## Step 1: Login as Root User

Login to the AWS Console using your Root Account.

---

## Step 2: Open IAM

In the AWS search bar, type:

```
IAM
```

Open the **Identity and Access Management (IAM)** service.

---

## Step 3: Navigate to Users

From the left navigation pane:

```
Users
```

Click:

```
Create User
```

---

## Step 4: Configure User Details

Enter:

```
User Name:
your-name
```

Example:

```
rahul
```

Select:

```
Provide user access to the AWS Management Console
```

Choose:

```
I want to create an IAM user
```

Set a custom password or let AWS generate one.

Click **Next**.

---

## Step 5: Assign Permissions

Choose:

```
Attach Policies Directly
```

Search for:

```
AdministratorAccess
```

Select:

```
AdministratorAccess
```

Click **Next**.

---

## Step 6: Review and Create

Review all details.

Click:

```
Create User
```

---

## Step 7: Download Login Details

Download or copy:

- IAM Username
- Console Login URL
- Password

These details will be required for future labs.

---

## Step 8: Login Using IAM User

Sign out of the Root User.

Open the IAM login URL.

Login using:

- Username
- Password

Verify that you can access the AWS Console.

---

## Lab Outcome

✅ IAM User Created

✅ AdministratorAccess Assigned

✅ Successfully logged in using IAM User

---

# Lab 3 – Launch an EC2 Instance

## Objective

Launch an Ubuntu EC2 instance that will be used as the Jenkins Server.

---

## Step 1: Open EC2 Dashboard

From the AWS Console, search for:

```
EC2
```

Open the EC2 Dashboard.

---

## Step 2: Launch Instance

Click:

```
Launch Instance
```

---

## Step 3: Configure Basic Details

Enter:

| Setting | Value |
|----------|-------|
| Name | jenkins-server |
| AMI | Ubuntu Server 24.04 LTS |
| Architecture | 64-bit (x86) |

---

## Step 4: Choose Instance Type

Select:

```
t3.micro
```

(Eligible under AWS Free Tier in many regions. If unavailable, use `t2.micro` where applicable.)

---

## Step 5: Create a Key Pair

Click:

```
Create New Key Pair
```

Configure:

```
Name:
jenkins-key
```

Type:

```
RSA
```

Format:

```
.pem
```

Click:

```
Create Key Pair
```

The key pair will automatically download to your computer.

> **Important:** Keep this `.pem` file safe. You will need it to SSH into the EC2 instance.

---

## Step 6: Configure Network Settings

Keep the default VPC and subnet.

Create or use the default Security Group.

Allow the following inbound rule:

| Type | Port |
|------|------|
| SSH | 22 |

(Optional for later labs)

| Type | Port |
|------|------|
| HTTP | 80 |

---

## Step 7: Configure Storage

Storage:

```
20 GB
```

Volume Type:

```
gp3
```

Leave the remaining settings as default.

---

## Step 8: Review Configuration

Verify:

- Instance Name
- Ubuntu 24.04
- t3.micro
- Key Pair Selected
- SSH Enabled
- 20 GB gp3 Storage

---

## Step 9: Launch Instance

Click:

```
Launch Instance
```

AWS will provision the virtual machine.

Wait until the instance state changes to:

```
Running
```

---

## Step 10: Verify Instance

Open the instance details.

Verify:

- Instance State = Running
- Status Checks = 2/2 Passed
- Public IPv4 Address is assigned

Copy the Public IP address.

It will be required in the next lab.

---

## Understanding the EC2 Instance

Your EC2 server includes:

- Virtual CPU (vCPU)
- RAM
- Operating System
- Elastic Block Storage (EBS)
- Network Interface
- Security Group (Firewall)

Think of EC2 as a virtual computer running in the AWS cloud.

---

## Lab Outcome

✅ EC2 Instance Launched

✅ Ubuntu Server Running

✅ Public IP Address Available

✅ Ready for SSH Connection

---

# Lab 4 – SSH into EC2

## Objective

Connect to the EC2 instance using SSH, verify the operating system, update the hostname, and check the Jenkins service status.

---

## Step 1: Navigate to the Key Pair Directory

Open **Command Prompt** (Windows) or **Terminal** (Linux/macOS) and navigate to the directory where your downloaded key pair (`.pem`) file is stored.

```bash
cd Downloads
```

> Replace the directory if your key pair is stored in a different location.

---

## Step 2: Connect to the EC2 Instance

Use the following SSH command to connect to your Ubuntu EC2 instance.

```bash
ssh -i <key-pair.pem> ubuntu@<public-ip>
```

Replace:

- `<key-pair.pem>` with your downloaded key pair file.
- `<public-ip>` with the Public IPv4 address of your EC2 instance.

Example:

```bash
ssh -i jenkins-key.pem ubuntu@54.xxx.xxx.xxx
```

If prompted with:

```
Are you sure you want to continue connecting (yes/no)?
```

Type:

```text
yes
```

---

## Step 3: Verify the Logged-in User

Run the following command:

```bash
whoami
```

Expected output:

```text
ubuntu
```

---

## Step 4: Verify the Operating System

Check the Linux distribution installed on the EC2 instance.

```bash
cat /etc/os-release
```

This command displays information such as:

- Operating System Name
- Version
- Ubuntu Release

---

## Step 5: Rename the Hostname

Set the hostname of the server to **jenkins**.

```bash
sudo hostnamectl set-hostname jenkins
```

---

## Step 6: Reload the Shell

Reload the current shell session.

```bash
bash
```

---

## Step 7: Verify Jenkins Service Status

Check whether the Jenkins service is installed and running.

```bash
sudo systemctl status jenkins
```

---

## Lab Outcome

✅ Successfully connected to the EC2 instance using SSH

✅ Verified the logged-in user

✅ Verified the operating system

✅ Updated the server hostname to **jenkins**

✅ Checked the Jenkins service status

---

# Installing Nginx

## Objective

Install the Nginx web server on the Ubuntu EC2 instance and verify that it is running successfully.

---

## Step 1: Update Package Repository

Update the package index.

```bash
sudo apt update -y
```

---

## Step 2: Install Nginx

Install the Nginx package.

```bash
sudo apt install nginx -y
```

---

## Step 3: Verify Nginx Service

Check whether the Nginx service is running.

```bash
sudo systemctl status nginx
```

You should see that the service is **active (running)**.

---

## Step 4: Verify from the Browser

Open your web browser and navigate to:

```text
http://<PUBLIC-IP>
```

Replace `<PUBLIC-IP>` with the public IP address of your EC2 instance.

If the installation is successful, you should see the **default Nginx Welcome Page**.

---

## Lab Outcome

✅ Nginx installed successfully

✅ Nginx service is running

✅ Successfully accessed the Nginx default page using the EC2 Public IP

---

# Summary

By the end of these notes, you should understand:

- Jenkins fundamentals
- CI/CD concepts
- Jenkins Pipelines
- Jenkins Plugins
- Distributed Builds
- Build Triggers
- Cloud Service Models
- Prompt Engineering Basics
- AI Models
- AWS EC2 Basics
- SSH into Linux
- Nginx Installation

---


# DevOps Lab Manual

---

# Lab 5 - Install Jenkins on an Ubuntu EC2 Instance

## Objective

Install Java and Jenkins on an Ubuntu EC2 instance and access the Jenkins dashboard from a browser.

---

## Prerequisites

- Ubuntu EC2 instance
- SSH access
- Security Group with:
  - SSH (22)
  - HTTP (80) (optional)
  - Custom TCP 8080 (required for Jenkins)

---

## Step 1 - Update the Server

```bash
sudo apt update
sudo apt upgrade -y
```

---

## Step 2 - Install Java

```bash
sudo apt install -y fontconfig openjdk-21-jre
```

Verify Java installation:

```bash
java -version
```

---

## Troubleshooting

### Scenario 1 - Java installation failed

Prompt:

> OpenJDK installation failed on Ubuntu EC2. How do I fix it?

---

### Scenario 2 - Permission denied

Prompt:

> Permission denied while installing packages on Ubuntu EC2.

---

## Step 3 - Install Jenkins

Add the Jenkins repository.

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
```

Add the repository.

```bash
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
```

Update packages.

```bash
sudo apt update
```

Install Jenkins.

```bash
sudo apt install -y jenkins
```

---

## Step 4 - Verify Jenkins

```bash
sudo systemctl status jenkins
```

Enable Jenkins at boot.

```bash
sudo systemctl enable jenkins
```

---

## Step 5 - Access Jenkins

Open:

```
http://<Public-IP>:8080
```

Example

```
http://13.233.xxx.xxx:8080
```

> **Note:** Ensure port **8080** is allowed in the EC2 Security Group inbound rules.

---

# Lab 6 - Change EC2 Instance Type

## Objective

Resize an EC2 instance.

---

## Steps

1. Stop the EC2 instance.
2. Go to

```
EC2 → Instance → Actions → Instance Settings → Change Instance Type
```

3. Change

```
t3.micro
```

to

```
t3.medium
```

Specifications

- 2 vCPUs
- 4 GB RAM

---

### Free Tier Note

If `t3.medium` is unavailable, choose one of:

- c7i-flex.large
- m7i-flex.large

---

4. Save changes.

5. Start the instance again.

---

# Lab 7 - Initialize Jenkins

## Step 1

Get the initial admin password.

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy the password.

---

## Step 2

Open

```
http://<Public-IP>:8080
```

Paste the password.

---

## Step 3

Click

```
Install Suggested Plugins
```

---

## Step 4

Create an administrator account.

Save the following safely:

- Username
- Password

These credentials will be required later.

---

# Git and GitHub Introduction

Typical CI/CD Flow

```
GitHub Repository
        ↓
Jenkins Build
        ↓
Run Tests
        ↓
Docker Build
        ↓
Push Docker Image to Docker Hub
        ↓
Deploy to EC2 / Kubernetes / Terraform
```

---

## Why Git?

Imagine five developers editing the same project.

Without Git:

- Code gets overwritten
- Conflicts occur
- Changes are lost
- Collaboration becomes difficult

Git enables teams to collaborate safely.

---

## What is Git?

Git is a Version Control System that tracks changes in source code.

### Real-world Analogy

Google Docs allows multiple people to:

- Edit simultaneously
- View history
- Restore previous versions

Git provides similar capabilities for source code.

---

## Git Workflow

```
Working Directory
        ↓
git add
        ↓
Staging Area
        ↓
git commit
        ↓
Local Repository
        ↓
git push
        ↓
Remote Repository (GitHub)
```

---

# Lab 8A - Create a Local Git Repository

## Objective

Initialize a Git repository and make the first commit.

### Create a project

```bash
mkdir my-project
cd my-project
```

Create files.

```bash
echo "This is File1" > file1.txt
echo "This is File2" > file2.txt
```

Initialize Git.

```bash
git init
```

Check status.

```bash
git status
```

Stage files.

```bash
git add .
```

Commit.

```bash
git commit -m "Initial commit"
```

---

## AI Prompts

- Explain git add vs git commit in simple terms.
- Explain the Git workflow with an example.

---

# Lab 8B - Connect Local Repository to GitHub

## HTTPS Authentication

```bash
git remote add origin https://github.com/<username>/<repo>.git
```

Push.

```bash
git push -u origin main
```

GitHub may ask for a Personal Access Token (PAT).

---

## SSH Authentication

Generate keys.

```bash
ssh-keygen -t rsa -b 4096
```

View public key.

```bash
cat ~/.ssh/id_rsa.pub
```

Add the key to GitHub.

Test connection.

```bash
ssh -T git@github.com
```

Update remote.

```bash
git remote remove origin

git remote add origin git@github.com:<username>/<repo>.git
```

Push.

```bash
git push -u origin main
```

---

# Lab 8C - Branching and Merging

Create a branch.

```bash
git checkout -b feature1
```

Create another branch.

```bash
git checkout -b feature2
```

Switch branches.

```bash
git switch feature1
```

Merge.

```bash
git checkout main
git merge feature1
```

---

## Pull Request Workflow

```
Developer
      ↓
Feature Branch
      ↓
Push
      ↓
Pull Request
      ↓
Review
      ↓
Approve / Reject
      ↓
Merge
```

---

# Lab 8D - Git Reset

## Soft Reset

```bash
git reset --soft HEAD~1
```

Undo commit while keeping changes staged.

---

## Mixed Reset

```bash
git reset --mixed HEAD~1
```

Undo commit and unstage files.

---

## Hard Reset

```bash
git reset --hard HEAD~1
```

Deletes the last commit and all associated changes.

---

## AI Prompt

Explain all Git reset modes with examples.

---

# Lab 8E - Merge Conflicts

## Create Conflict

On `feature2`

```bash
echo "Change from feature2" > file8.txt
```

Commit.

Switch to `feature3`

```bash
echo "Change from feature3" > file8.txt
```

Commit.

Merge both branches into `main`.

Git reports a merge conflict.

---

## Resolve Conflict

Open the conflicted file.

Remove:

```
<<<<<<<
=======
>>>>>>>
```

Save.

Stage.

```bash
git add file8.txt
```

Commit.

```bash
git commit
```

---

## AI Prompt

Resolve the following Git merge conflict.

Paste the error message into ChatGPT.

---

# Lab 8F - Merge Strategies

## Normal Merge

All commits remain.

```
A
 \
  B1
  B2
  B3
```

History contains all commits.

---

## Squash Merge

```
A
 \
  B1
  B2
  B3
        ↓
     Single Commit
```

History remains clean.

---

## Rebase

Moves commits from one branch onto another to create a linear history.

Example:

```bash
git checkout feature1
git rebase main
```

---

## Practice Commands

Practice the following:

- git status
- git log
- git diff
- git branch
- git switch
- git checkout
- git merge
- git pull
- git push
- git reset
- git remote
- git add
- git commit

---

# Suggested GenAI Prompts

1. Explain Git like I am a beginner.
2. Difference between Git and GitHub.
3. Explain Git branches with diagrams.
4. Explain Git merge vs rebase.
5. Explain Git reset with examples.
6. How does Git resolve merge conflicts?
7. Explain Git staging area with examples.
8. Best practices for Git commit messages.




# Docker Fundamentals

## Overview

Docker is a containerization platform that packages an application along with all its dependencies into a **container**. Containers provide a consistent runtime environment, ensuring the application behaves the same on every machine.

---

# Why Do We Need Docker?

### Scenario

You developed a web application using:

- Node.js
- HTML
- CSS
- JavaScript

The application works perfectly on your laptop.

**Question:** Will it run the same on another developer's laptop?

**Answer:** Maybe.

The application may fail because of:

- Different Node.js versions
- Missing dependencies
- Different operating system
- Missing environment variables
- Different package versions

Docker solves this problem by packaging the application and its dependencies together.

**Build Once → Run Anywhere**

---

# Virtual Machines vs Containers

| Virtual Machine | Docker Container |
|-----------------|------------------|
| Includes complete Guest OS | Shares Host OS Kernel |
| Heavy | Lightweight |
| Slow startup | Starts in seconds |
| High resource usage | Low resource usage |
| Large image size | Small image size |
| Hardware Virtualization | OS-level Virtualization |

---

# What is Docker?

Docker is a platform used to package an application along with its dependencies into a portable container.

Think of it like a **shipping container**.

Just as a shipping container carries goods safely across the world, Docker containers carry your application and everything it needs to run.

A Docker container may include:

- Application Code
- Libraries
- Runtime
- Environment Variables
- Dependencies
- Configuration Files

---

# Docker Image vs Docker Container

## Docker Image

A Docker Image is a **blueprint** or **template** used to create containers.

It contains:

- Application
- Runtime
- Dependencies
- Libraries
- Configuration

Example:

```
ubuntu
nginx
python:3.12
node:20
```

---

## Docker Container

A Docker Container is a **running instance** of a Docker Image.

Example:

```
Image
   ↓
docker run
   ↓
Container
```

Real-life analogy:

```
Class  → Object

Image  → Container
```

---

# Docker Workflow

```
Write Application
        ↓
Create Dockerfile
        ↓
Build Image
        ↓
Run Container
        ↓
Deploy Anywhere
```

---

# Lab 1 – Install Docker on Ubuntu / EC2

Official Documentation:

https://docs.docker.com/engine/install/ubuntu/

### Step 1 – Update Packages

```bash
sudo apt update
sudo apt install ca-certificates curl
```

### Step 2 – Add Docker Repository

```bash
sudo install -m 0755 -d /etc/apt/keyrings

sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg \
-o /etc/apt/keyrings/docker.asc

sudo chmod a+r /etc/apt/keyrings/docker.asc
```

```bash
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF
```

Update package list:

```bash
sudo apt update
```

### Step 3 – Install Docker

```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Step 4 – Verify Installation

```bash
docker --version

sudo systemctl status docker
```

---

## Run Docker Without sudo

```bash
sudo usermod -aG docker ubuntu

newgrp docker

sudo systemctl daemon-reload
```

Verify:

```bash
docker run hello-world
```

---

# Lab 2 – First Docker Container

Run:

```bash
docker run hello-world
```

What happens?

- Docker checks for the image locally.
- If not available, it downloads it from Docker Hub.
- Creates a new container.
- Executes the application.
- Exits automatically.

---

# Three Modes of Running Containers

## 1. Foreground Mode

```bash
docker run hello-world
```

or

```bash
docker run ubuntu
```

Characteristics:

- Runs in current terminal
- Displays logs
- Terminal remains occupied
- Stops when application exits

---

## 2. Detached Mode

Runs container in background.

```bash
docker run -d nginx
```

Interactive Ubuntu:

```bash
docker run -dt ubuntu
```

Useful Commands

```bash
docker ps

docker logs <container>

docker stop <container>
```

---

## 3. Interactive Mode

Launch container and immediately enter shell.

```bash
docker run -it ubuntu bash
```

Exit container:

```
Ctrl + P + Q
```

(keeps container running)

To stop:

```
exit
```

Reconnect:

```bash
docker attach <container-id>
```

or

```bash
docker exec -it <container-id> bash
```

`docker exec` is generally preferred because it opens a new shell without affecting the main container process.

---

# Frequently Used Docker Commands

## Images

```bash
docker pull nginx

docker images

docker rmi image-name
```

---

## Containers

```bash
docker run nginx

docker ps

docker ps -a

docker ps -l

docker ps -q

docker stop container

docker start container

docker restart container

docker rm container
```

---

## System Commands

```bash
docker system df

docker system prune

docker stats
```

---

# Lab 3 – Inspect Docker Objects

The `docker inspect` command displays detailed JSON metadata about Docker objects.

Inspect a container:

```bash
docker inspect <container-id>
```

Inspect an image:

```bash
docker inspect nginx
```

Useful examples:

Container IP Address

```bash
docker inspect -f '{{.NetworkSettings.IPAddress}}' <container>
```

Container Name

```bash
docker inspect -f '{{.Name}}' <container>
```

Container Status

```bash
docker inspect -f '{{.State.Status}}' <container>
```

Mounted Volumes

```bash
docker inspect -f '{{json .Mounts}}' <container>
```

Environment Variables

```bash
docker inspect -f '{{json .Config.Env}}' <container>
```

---

# Useful Commands

View Logs

```bash
docker logs <container>
```

Live Logs

```bash
docker logs -f <container>
```

Processes Running

```bash
docker top <container>
```

Copy Files

```bash
docker cp test.txt container:/tmp
```

Rename Container

```bash
docker rename old-name new-name
```

Container Resource Usage

```bash
docker stats
```


# Cgroups (Control Groups)

## Overview

**Cgroups (Control Groups)** are a Linux kernel feature that allows you to limit and monitor the resources consumed by processes. Docker uses cgroups to ensure that containers do not consume excessive CPU or memory.

### Example

Suppose your server has:

- 2 vCPUs
- 4 GB RAM
- 20 GB Storage

Running three containers:

- Frontend
- Backend
- Database

If one container consumes all the memory or CPU, the other containers may become slow or even crash. Cgroups help prevent this by enforcing resource limits.

---

## Limit Memory

Run a container with a maximum memory limit of 512 MB.

```bash
docker run -d --memory="512m" ubuntu sleep infinity
```

Verify the limit:

```bash
docker inspect <container-name>
```

---

## Limit CPU

Allow the container to use only half of one CPU core.

```bash
docker run -d --cpus="0.5" ubuntu sleep infinity
```

---

## Limit Number of Processes

```bash
docker run -d --pids-limit=100 ubuntu sleep infinity
```

---

## Update Resources of a Running Container

Increase memory:

```bash
docker update --memory="1g" <container-name>
```

Update CPU limit:

```bash
docker update --cpus="1" <container-name>
```

Check live resource usage:

```bash
docker stats
```

---

# Dockerfile

A **Dockerfile** is a text file containing instructions used to build a Docker Image.

Example:

```dockerfile
FROM python:3.12-trixie

WORKDIR /app

COPY . /app

RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 8080

CMD ["python3","app.py"]
```

### Build the Image

```bash
docker build -t demo-image:v1 .
```

Verify:

```bash
docker images
```

---

# Lab 4 – Run Your Image

Start a container from the image:

```bash
docker run -d -p 8080:8080 --name demo demo-image:v1
```

Verify:

```bash
docker ps
```

Open the application:

```
http://<Server-IP>:8080
```

Stop:

```bash
docker stop demo
```

Remove:

```bash
docker rm demo
```

---

# Create an Image from a Running Container

Sometimes changes are made manually inside a container.

Save those changes as a new image:

```bash
docker commit <container-id> myimage:v1
```

Verify:

```bash
docker images
```

---

# Docker Compose

Docker Compose helps run multiple containers using a single YAML file.

Start all services:

```bash
docker compose up
```

Start in detached mode:

```bash
docker compose up -d
```

Stop services:

```bash
docker compose down
```

View running services:

```bash
docker compose ps
```

---

# Push Images to Docker Hub

## Step 1 – Login

```bash
docker login
```

## Step 2 – Tag the Image

```bash
docker tag demo-image:v1 <dockerhub-username>/demo-image:v1
```

Example:

```bash
docker tag demo-image:v1 ajit0101/demo-image:v1
```

## Step 3 – Push the Image

```bash
docker push ajit0101/demo-image:v1
```

Anyone can now pull the image using:

```bash
docker pull ajit0101/demo-image:v1
```

---

# Additional Practice Labs

## Lab 5 – Run Nginx

```bash
docker run -d --name nginx-server -p 80:80 nginx
```

Verify:

```bash
docker ps
```

Open:

```
http://<Server-IP>
```

---

## Lab 6 – Port Mapping

Run Apache on port 8080:

```bash
docker run -d -p 8080:80 httpd
```

Open:

```
http://<Server-IP>:8080
```

---

## Lab 7 – Execute Commands Inside a Running Container

```bash
docker exec -it nginx-server bash
```

If `bash` is unavailable:

```bash
docker exec -it nginx-server sh
```

Check hostname:

```bash
hostname
```

Exit:

```bash
exit
```

---

## Lab 8 – View Container Logs

Generate logs:

```bash
docker logs nginx-server
```

Follow logs in real time:

```bash
docker logs -f nginx-server
```

---

## Lab 9 – Clean Up Docker Resources

Remove stopped containers:

```bash
docker container prune
```

Remove unused images:

```bash
docker image prune
```

Remove everything unused:

```bash
docker system prune -a
```

---

# Docker Workflow Summary

```
Write Application
        │
        ▼
Create Dockerfile
        │
        ▼
Build Image
docker build
        │
        ▼
Run Container
docker run
        │
        ▼
Test Application
        │
        ▼
Tag Image
docker tag
        │
        ▼
Push to Docker Hub
docker push
        │
        ▼
Deploy Anywhere
```

---

# Common Docker Commands

```bash
docker --version
docker images
docker pull <image>
docker build -t image-name .
docker run -d image-name
docker ps
docker ps -a
docker logs <container>
docker exec -it <container> bash
docker inspect <container>
docker stats
docker stop <container>
docker start <container>
docker restart <container>
docker rm <container>
docker rmi <image>
docker commit <container> image-name
docker compose up -d
docker compose down
docker login
docker tag
docker push
docker system prune -a
```

---

# Key Takeaways

- Docker packages applications with all dependencies.
- Images are templates; containers are running instances of images.
- Containers are lightweight compared to virtual machines.
- Use **Dockerfiles** to build custom images.
- Use **Docker Compose** for multi-container applications.
- Use **docker inspect** to view container metadata.
- Use **cgroups** to control CPU and memory usage.
- Push images to **Docker Hub** for sharing and deployment.
```

```

# Jenkins Dashboard, Freestyle Jobs, Parameters & Environment Variables

---

# Jenkins Dashboard and UI

## What is Jenkins?

Jenkins is an **open-source automation server** used to implement **Continuous Integration (CI)** and **Continuous Delivery/Deployment (CD)**. It automates repetitive tasks such as building applications, running tests, and deploying software.

One of Jenkins' biggest strengths is its plugin ecosystem, which allows it to integrate with hundreds of different tools.

### Key Features

- Open-source and free to use
- Supports CI/CD pipelines
- More than **2,000 plugins** available
- Easy integration with Git, Docker, Kubernetes, Maven, SonarQube, Slack, AWS, and many more tools
- Supports distributed builds using multiple agents

---

# What is a Jenkins Job?

A **Jenkins Job** is a task or automation that Jenkins executes.

A job contains a sequence of steps that Jenkins performs automatically whenever the job is triggered.

### Examples of Jenkins Jobs

- Build an application
- Run automated tests
- Execute shell scripts
- Package an application
- Deploy an application
- Send notifications after build completion

For example, in a Node.js application a Jenkins job may execute:

```bash
npm install
npm start
```

or

```bash
npm install
npm test
npm run build
```

---

# Jenkins Controller and Agents

Think of Jenkins like a **manager** in a company.

- The **Controller (Master)** receives work.
- It assigns jobs to available **Agents (Workers)**.
- Agents execute the tasks and return the results back to the controller.

```
               Jenkins Controller
                      │
        ┌─────────────┼─────────────┐
        │             │             │
     Agent 1       Agent 2       Agent 3
```

The Jenkins Controller can run on:

- Linux
- Windows
- macOS

Jenkins itself is a **Java application**, so Java must be installed before installing Jenkins.

---

# Lab Only: Disable Jenkins Authentication (Not Recommended)

> **Warning**
>
> This method should only be used in a **practice or lab environment**. Never disable Jenkins authentication on a production server.

### Step 1

Stop the Jenkins service.

```bash
sudo systemctl stop jenkins.service
```

### Step 2

Open the Jenkins configuration file.

```bash
sudo nano /var/lib/jenkins/config.xml
```

### Step 3

Locate:

```xml
<useSecurity>true</useSecurity>
```

Change it to:

```xml
<useSecurity>false</useSecurity>
```

### Step 4

Save the file.

### Step 5

Start Jenkins again.

```bash
sudo systemctl start jenkins.service
```

After restarting, Jenkins will no longer ask for user authentication.

---

# Jenkins Labs

---

# LAB 1 – Installing Jenkins on Ubuntu Linux

Refer to the GitHub repository for the installation steps.

Repository:

https://github.com/ajit010/Jenkins-6th-july.git

Complete the installation before moving to the next lab.

---

# LAB 2 – Initial Setup and Unlocking Jenkins

Complete the initial Jenkins setup by following the instructions provided in the GitHub repository.

Tasks include:

- Unlock Jenkins
- Install suggested plugins
- Create the first administrator user
- Log in to the Jenkins Dashboard

---

# LAB 3 – Exploring the Jenkins Dashboard and UI

Spend some time understanding the Jenkins interface.

Important sections include:

## Jobs

Jenkins supports different job types, including:

- Freestyle Project
- Pipeline
- Multibranch Pipeline
- Folder
- Organization Folder

---

## Build History

Displays all previous builds.

Example:

```
#1
#2
#3
```

You can click any build to view:

- Build status
- Console Output
- Build duration
- Build artifacts
- Build logs

---

## Manage Jenkins

This section contains all administration options.

Common settings include:

- System Configuration
- Global Tool Configuration
- Environment Variables
- Nodes
- Credentials
- Plugins
- Security
- Cloud Configuration

Spend a few minutes exploring each option.

---

# LAB 4 – Creating Your First Freestyle Job

### Step 1

Click **New Item** (or **Create a New Job**).

### Step 2

Enter the job name.

Example:

```
hello-world-job
```

Select:

```
Freestyle Project
```

Click **OK**.

---

### Step 3

Under **Description**, enter:

```
My first Jenkins job
```

---

### Step 4

Scroll to **Build Steps**

Click

```
Add Build Step
```

Choose

```
Execute Shell
```

Paste:

```bash
echo "Hello World from Jenkins"
echo "Today is $(date)"
echo "Running on host: $(hostname)"
```

---

### Step 5

Click **Save**.

---

### Step 6

Click

```
Build Now
```

The build will appear in the Build History section.

Open the build and verify the output.

---

# LAB 5 – Reading Console Output and Build Status

After a build completes, Jenkins displays its status.

## Successful Build

Displayed with a **blue/green icon** depending on the Jenkins theme.

## Failed Build

Displayed with a **red icon**.

---

Open the build.

Click:

```
Console Output
```

Review every step executed by Jenkins.

The console log contains:

- Commands executed
- Output generated
- Errors
- Exit status
- Build duration

---

## Troubleshooting Tip

If a build fails:

1. Download the console log.
2. Upload it to ChatGPT or Claude.
3. Use a prompt like:

```
Analyze this Jenkins build log.

Identify the root cause of the failure and provide step-by-step troubleshooting instructions with possible fixes.
```

This is an effective way to learn how to debug Jenkins jobs.

---

# LAB 6 – Multiple Build Steps in One Job

A Jenkins job can contain multiple build steps.

Create three separate **Execute Shell** build steps.

---

## Shell Step 1

```bash
echo "Step 1: Preparing Environment"

mkdir -p /tmp/jenkins-demo
```

---

## Shell Step 2

```bash
echo "Step 2: Creating a file"

echo "Build data: $(date)" > /tmp/jenkins-demo/output.txt
```

---

## Shell Step 3

```bash
echo "Step 3: Displaying the file"

cat /tmp/jenkins-demo/output.txt
```

---

Build the job.

Observe how Jenkins executes each build step sequentially.

---

# LAB 7 – Parameterized Builds

Parameterized builds allow users to provide input values before starting a build.

Instead of creating multiple jobs for different environments or users, a single job can accept parameters.

---

## Step 1

Create a new Freestyle Project.

Name it:

```
parameterized-job
```

---

## Step 2

Under **General**

Enable:

```
This project is parameterized
```

---

## Step 3

Add a **String Parameter**

Name:

```
USERNAME
```

Default Value:

```
student
```

Description:

```
Your name
```

---

## Step 4

Add a **Choice Parameter**

Name:

```
ENVIRONMENT
```

Choices:

```
dev
staging
prod
```

---

## Step 5

Add a **Boolean Parameter**

Name:

```
VERBOSE
```

Leave it unchecked by default.

---

## Step 6

Add an **Execute Shell** build step.

```bash
echo "Hello, $USERNAME"

echo "Deploy target: $ENVIRONMENT"

if [ "$VERBOSE" = "true" ]; then
    echo "Verbose mode enabled"
    env | sort | head -20
fi
```

---

## Step 7

Save the job.

Notice the left menu now shows:

```
Build with Parameters
```

Click it.

Try different combinations of:

- USERNAME
- ENVIRONMENT
- VERBOSE

Observe how the build output changes based on the selected values.

---

## Real-World Example

Imagine the same application needs to be deployed to different environments.

Example infrastructure:

| Environment | Server Configuration |
|------------|----------------------|
| Development | 4 vCPU, 16 GB RAM |
| Production | 16 vCPU, 64 GB RAM |

Instead of creating multiple Jenkins jobs, one parameterized job can deploy to different environments by selecting:

- dev
- staging
- prod

This approach makes Jenkins jobs more reusable and easier to maintain.

---

# LAB 8 – Working with Jenkins Environment Variables

Jenkins automatically provides several built-in environment variables during every build.

These variables provide useful information about the current job and build.

---

## Step 1

Create a Freestyle Project named:

```
env-explorer
```

---

## Step 2

Add an **Execute Shell** build step.

```bash
echo "JOB_NAME = $JOB_NAME"

echo "BUILD_NUMBER = $BUILD_NUMBER"

echo "BUILD_ID = $BUILD_ID"

echo "BUILD_URL = $BUILD_URL"

echo "WORKSPACE = $WORKSPACE"

echo "JENKINS_URL = $JENKINS_URL"

echo "NODE_NAME = $NODE_NAME"
```

---

## Step 3

Add another Execute Shell step.

```bash
env | sort
```

This prints all available environment variables.

---

## Step 4

Save the job.

Click **Build Now**.

Study the Console Output.

---

## Step 5

Open the following URL in your browser:

```
http://<server-ip>:8080/env-vars.html
```

This page lists all Jenkins environment variables available during a build.

---

## Step 6

Run the job twice.

Observe:

- `BUILD_NUMBER` increases with every build.
- `JOB_NAME` remains the same.

---

# Linux Environment Variables

You can also create your own environment variables in Linux.

Create a variable:

```bash
export DB_USERNAME=ajit_db
```

Verify it:

```bash
echo $DB_USERNAME
```

If the value is displayed, the environment variable has been successfully created.

> **Note:** Variables created using `export` are temporary and exist only for the current shell session unless added to shell configuration files such as `.bashrc` or `.profile`.

---


# LAB 9 – Scheduling Builds Using Cron

Jenkins can automatically trigger jobs on a schedule using **Cron expressions**. This is useful for running builds, backups, health checks, or automated tasks without manual intervention.

> **Example Use Cases**
>
> - Nightly builds
> - Daily backups
> - Running automated tests every few hours
> - Health check scripts
> - Scheduled deployments

---

## Understanding Cron Syntax

A cron expression consists of **five fields**:

```
MINUTE   HOUR   DAY_OF_MONTH   MONTH   DAY_OF_WEEK
```

Example:

```text
* * * * *
```

This means **run every minute**.

---

## Step 1

Create a new **Freestyle Project** named:

```
scheduled-job
```

---

## Step 2

Add an **Execute Shell** build step.

```bash
echo "Scheduled run at $(date)"
```

---

## Step 3

Scroll to **Build Triggers**.

Enable:

```
Build periodically
```

Enter the following schedule:

```text
H/2 * * * *
```

This runs the job approximately every **2 minutes**.

---

## What does `H` mean?

Unlike standard Linux cron, Jenkins supports the **H (Hash)** symbol.

Instead of triggering every job at the exact same time, Jenkins distributes jobs across different minutes to reduce server load.

For example:

```
H/2 * * * *
```

means:

> Run every 2 minutes, but choose the starting minute automatically.

---

## Step 4

Save the job.

Wait for **5–10 minutes**.

Jenkins should automatically trigger the build.

The build history will show:

```
Started by timer
```

---

## More Cron Examples

### Every day at 2:30 AM

```text
30 2 * * *
```

---

### Every weekday at 9:00 AM

```text
0 9 * * 1-5
```

---

### Twice a day (Load Balanced)

```text
H H(0-7)/12 * * *
```

---

## Stop Scheduled Builds

To stop automatic execution:

- Remove the cron expression, or
- Comment it out

Then save the job.

---

# LAB 10 – Installing and Managing Plugins

One of Jenkins' biggest strengths is its **plugin ecosystem**.

Plugins extend Jenkins by adding support for additional tools and technologies.

Examples include:

- Docker
- Kubernetes
- Git
- Maven
- SonarQube
- Slack
- AWS
- Build Timestamp
- Docker Pipeline

---

## Step 1

Navigate to:

```
Manage Jenkins
```

↓

```
Plugins
```

---

## Step 2

Search for and install plugins such as:

- Git
- Docker
- Docker Pipeline
- Build Timestamp

> **Tip**
>
> Install only the plugins you actually need. Too many unused plugins increase maintenance effort and may introduce compatibility issues.

---

## Step 3

Restart Jenkins after installation.

```bash
sudo systemctl restart jenkins
```

Wait for **1–2 minutes**, then open:

```
http://<Public-IP>:8080
```

Sign in using your Jenkins credentials.

---

# LAB 11 – Cloning a Git Repository Using a Freestyle Job

In this lab, Jenkins will clone source code directly from a GitHub repository.

We will use the official Jenkins sample project:

Repository:

```
https://github.com/jenkins-docs/simple-java-maven-app.git
```

---

## Prerequisites

- Jenkins installed and running
- Git installed on the Jenkins server
- Git Plugin installed in Jenkins

Verify Git installation:

```bash
git --version
```

---

## Step 1

Create a Freestyle Project.

Name it:

```
git-clone-demo
```

---

## Step 2

Under:

```
Source Code Management
```

Select:

```
Git
```

---

## Step 3

Repository URL

```
https://github.com/jenkins-docs/simple-java-maven-app.git
```

---

## Step 4

Since the repository is public:

- Leave **Credentials** empty.
- Set **Branch Specifier** to:

```text
*/master
```

---

## Step 5

Add an **Execute Shell** build step.

```bash
pwd

ls -la

git log --oneline -5
```

This verifies that Jenkins successfully cloned the repository.

---

## Step 6

Click:

```
Build Now
```

Watch the Console Output.

You will notice Jenkins first performs the Git clone operation before executing the shell commands.

---

## Step 7

Open:

```
Workspace
```

from the left menu.

Browse the cloned project files directly from the Jenkins UI.

---

# LAB 12 – Polling SCM for Changes

Instead of scheduling builds at fixed times, Jenkins can periodically check a Git repository and trigger a build **only when new commits are detected**.

This feature is called **Poll SCM**.

---

## Step 1

Fork the repository into your own GitHub account.

```
https://github.com/jenkins-docs/simple-java-maven-app.git
```

---

## Step 2

Use the Jenkins job created in **Lab 11**.

Update the repository URL so that it points to **your fork**.

---

## Step 3

Go to:

```
Build Triggers
```

Enable:

```
Poll SCM
```

Use the schedule:

```text
H/2 * * * *
```

Jenkins will check GitHub approximately every two minutes.

---

## Step 4

Click:

```
Git Polling Log
```

Initially you should see:

```
No changes
```

---

## Step 5

Open GitHub.

Edit the **README.md** file.

Commit the change directly from GitHub.

---

## Step 6

Wait a few minutes.

Jenkins detects the new commit.

A new build starts automatically.

Build Cause:

```
Started by an SCM change
```

This means Jenkins detected changes in the repository and triggered the build automatically.

---

# LAB 13 – Installing Maven and Building a Java Project

In this lab, Jenkins will build a real Java application using **Apache Maven**.

---

## Install Maven on the Jenkins Server

```bash
sudo apt update

sudo apt install -y maven
```

Verify installation:

```bash
mvn --version
```

---

## Alternative Method (Recommended)

Instead of installing Maven manually, Jenkins can install and manage Maven automatically.

Navigate to:

```
Manage Jenkins
```

↓

```
Tools
```

↓

```
Maven Installations
```

Click:

```
Add Maven
```

Example name:

```
maven-3.9
```

Enable:

```
Install automatically
```

Jenkins downloads Maven whenever required.

---

## Repository

Use the following GitHub repository:

```
https://github.com/ajit010/devops-maven-docker.git
```

---

## Configure the Job

Update the repository URL to the Maven project.

---

## Build Step

Add an **Execute Shell** build step.

```bash
mvn clean

mvn package
```

or

```bash
mvn clean package
```

---

## Build the Project

Click:

```
Build Now
```

If the build succeeds, Maven creates the project artifact.

---

## Verify the Output

Open the workspace directory:

```text
/var/lib/jenkins/workspace/<your-job-name>
```

Navigate to:

```text
target/
```

You should see the generated application artifact such as:

```
.war
```

or

```
.jar
```

depending on the project packaging type.

---

# Docker vs Kubernetes

Understanding the difference between Docker and Kubernetes is important for modern DevOps workflows.

---

## Docker

Docker runs containers on a **single host machine**.

Example:

```
EC2 Instance
    │
Docker Engine
    │
Containers
```

If the EC2 instance is stopped:

- All containers stop.
- When the server starts again, containers remain stopped.
- Containers must be started manually.

Example:

```bash
docker start <container-name>
```

Docker by itself does **not** provide automatic container recovery after a host restart.

---

## Kubernetes

Kubernetes manages containers across **multiple machines (nodes)**.

A Kubernetes cluster typically consists of:

- Control Plane (Master Node)
- Worker Nodes

```
Control Plane
        │
 ┌──────┴──────┐
 │             │
Worker 1    Worker 2
 │             │
Pods         Pods
```

If one worker node goes down:

- Kubernetes detects the failure.
- The affected Pods are automatically recreated.
- Workloads are scheduled on healthy worker nodes.
- Applications remain available with minimal downtime.

---

## Why Kubernetes?

Kubernetes provides features such as:

- High Availability (HA)
- Automatic Self-Healing
- Auto Scheduling
- Scaling
- Rolling Updates
- Load Balancing

Unlike Docker alone, Kubernetes continuously monitors the desired state of applications and works to maintain it automatically.

---

# Summary

In this session, you learned how to:

- Schedule Jenkins jobs using Cron expressions
- Understand the purpose of the `H` symbol in Jenkins Cron
- Install and manage Jenkins plugins
- Clone Git repositories using Jenkins
- Automatically trigger builds using Poll SCM
- Install and configure Maven
- Build a Java project using Maven
- Locate generated build artifacts (`.jar` / `.war`)
- Understand the key differences between Docker and Kubernetes
- Learn why Kubernetes provides high availability and self-healing compared to Docker alone

---
