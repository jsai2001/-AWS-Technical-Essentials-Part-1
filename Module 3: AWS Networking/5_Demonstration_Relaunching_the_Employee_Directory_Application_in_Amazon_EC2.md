# Relaunching the Employee Directory Application in Amazon EC2

## Overview

Demonstration of creating a custom VPC and relaunching the employee directory application with proper networking configuration.

## Step 1: Create VPC

1. Navigate to VPC Dashboard → Create VPC
2. Select "VPC only"
3. **Name:** app-vpc
4. **CIDR:** 10.1.0.0/16
5. Create VPC

## Step 2: Create Subnets

Create 4 subnets across 2 Availability Zones:

| Subnet Name | AZ | CIDR | Type |
|-------------|----|----- |------|
| Public Subnet 1 | us-west-2a | 10.1.1.0/24 | Public |
| Private Subnet 1 | us-west-2a | 10.1.2.0/24 | Private |
| Public Subnet 2 | us-west-2b | 10.1.3.0/24 | Public |
| Private Subnet 2 | us-west-2b | 10.1.4.0/24 | Private |

## Step 3: Create Internet Gateway

1. Navigate to Internet Gateways → Create internet gateway
2. **Name:** app-igw
3. Attach to app-vpc
4. **Note:** One-to-one relationship (1 IGW per VPC)

## Step 4: Configure Route Tables

### Create Public Route Table
1. **Name:** public-route-table
2. **VPC:** app-vpc
3. **Add Route:**
   - Destination: 0.0.0.0/0
   - Target: app-igw
4. **Associate:** Public Subnet 1 and Public Subnet 2

### Key Concept
Subnets are public/private based on route table associations, not inherent properties.

## Step 5: Relaunch EC2 Instance

### Launch Configuration
1. Use "Launch more like this" from existing instance
2. **Name:** Employee Directory App 2
3. **AMI:** Amazon Linux 2
4. **Instance Type:** t2.micro
5. **Key Pair:** Proceed without key pair

### Network Settings
- **VPC:** app-vpc
- **Subnet:** Public Subnet 1
- **Auto-assign Public IP:** Enable
- **Security Group:** Create new (old SG tied to default VPC)

### Security Group Rules
| Type | Protocol | Port | Source |
|------|----------|------|--------|
| HTTP | TCP | 80 | 0.0.0.0/0 |
| HTTPS | TCP | 443 | 0.0.0.0/0 |

### Advanced Settings
- **IAM Role:** Pre-populated from original instance
- **User Data:** Pre-populated application setup script

## Verification

1. Wait for instance to reach "running" state
2. Copy public IP address
3. Access application via browser
4. Successful access confirms proper network configuration

## Key Takeaways

- **Security Groups are VPC-specific** - Cannot reuse across VPCs
- **Route tables determine accessibility** - Not subnet properties
- **High availability** - Resources across multiple AZs
- **Custom VPC benefits** - Better security than default VPC