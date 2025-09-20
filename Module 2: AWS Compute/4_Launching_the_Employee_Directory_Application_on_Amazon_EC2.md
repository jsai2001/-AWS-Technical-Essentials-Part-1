# Launching the Employee Directory Application on Amazon EC2

## EC2 Instance Configuration

### Step 1: Basic Settings
- **Name:** employee-directory-app
- **AMI:** Amazon Linux 2023 (free tier eligible)
- **Instance Type:** t2.micro (free tier eligible)
- **Key Pair:** Proceed without key pair (use console connect)

### Step 2: Network Settings
- **VPC:** Default VPC (has internet gateway)
- **Subnet:** Default subnet (public access)
- **Auto-assign Public IP:** Enable
- **Security Group:** Create new with HTTP/HTTPS inbound rules (disable SSH)

### Step 3: Storage
- **Root Volume:** Default EBS volume
- **Additional Storage:** None

### Step 4: Advanced Configuration
- **IAM Instance Profile:** EmployeeWebAppRole (S3 + DynamoDB permissions)
- **User Data:** Bash script for application setup

## User Data Script

```bash
#!/bin/bash
wget https://s3-bucket/employee-app.zip
unzip employee-app.zip
cd employee-directory-app
yum install -y python3 pip
pip install -r requirements.txt
yum install -y stress
export PHOTOS_BUCKET=placeholder
export AWS_DEFAULT_REGION=us-west-2
export DYNAMO_MODE=on
python3 application.py --port 80
```

### Script Functions
1. Download application code from S3
2. Install Python 3 and pip
3. Install Flask dependencies
4. Install stress tool (for autoscaling demos)
5. Set environment variables
6. Start application on port 80

## Launch Process

1. Click "Launch instance"
2. Wait for instance state: **Running**
3. Wait for status checks: **Passed**
4. Access via public IP address

## Expected Result

- Empty employee directory application loads
- Ready for S3 bucket and DynamoDB integration
- Accessible via HTTP on public IP