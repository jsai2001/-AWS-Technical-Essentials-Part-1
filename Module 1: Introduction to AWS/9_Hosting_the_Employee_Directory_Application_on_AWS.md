# Hosting the Employee Directory Application on AWS

## Overview

This demonstration shows how to host an application using Amazon EC2 with default AWS configurations.

## EC2 Instance Setup

### Step 1: Launch Instance
1. Navigate to EC2 console → Launch instance
2. Name: `employee-web-app`
3. Select free tier eligible Linux AMI
4. Instance type: `t2.micro` (free tier)

### Step 2: Key Pair
- Select "Proceed without a key pair" (no SSH needed)

### Step 3: Network Settings
- **VPC:** Use default VPC
- **Subnet:** No preference
- **Security Group:** Create new with HTTP/HTTPS inbound rules

### Step 4: Advanced Configuration
- **IAM Instance Profile:** Select application role
- **User Data:** Script to:
  - Download application source code
  - Start web server
  - Initialize application

### Step 5: Launch
- Click "Launch instance"
- Wait for instance to boot up
- Access via public IP address in browser

## Key Concepts

**Default VPC:** AWS-provided private network for resources  
**EC2 Instance:** Single virtual machine  
**AMI:** Amazon Machine Image (OS template)  
**Security Group:** Instance-level firewall  
**User Data:** Boot-time automation script  

## Expected Result

- Application homepage loads (no data initially)
- Ready for database integration in later lessons