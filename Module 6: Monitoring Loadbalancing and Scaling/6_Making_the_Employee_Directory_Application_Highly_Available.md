# Making the Employee Directory Application Highly Available

## Overview
Implementation guide for configuring high availability using Application Load Balancer (ALB) and Auto Scaling for the Employee Directory application.

## Architecture Components
- **Application Load Balancer**: Distributes traffic across multiple instances
- **Target Groups**: Manages health checks and routing
- **Auto Scaling Group**: Automatically manages instance capacity
- **Launch Template**: Defines instance configuration for scaling

## Implementation Steps

### 1. Launch Application Instance
```
Instance Name: employee-directory-app-lb
Configuration: Use existing instance as template
Network: Enable public IP for testing
Role: Ensure instance role is attached
User Data: Application bootstrap script
```

### 2. Create Application Load Balancer

#### Basic Configuration
```
Name: app-elb
Scheme: Internet-facing
VPC: app-vpc
Availability Zones: us-west-2a, us-west-2b
Subnets: Public subnets in selected AZs
```

#### Security Group Configuration
```
Name: load-balancer-sg
Description: HTTP access for load balancer
VPC: app-vpc
Inbound Rules: HTTP (port 80) from 0.0.0.0/0
```

### 3. Create Target Group

#### Target Group Settings
```
Name: app-target-group
Target Type: Instances
VPC: app-vpc
Protocol: HTTP
Port: 80
```

#### Health Check Configuration
```
Healthy Threshold: 2 consecutive successful checks
Unhealthy Threshold: 5 consecutive failed checks
Timeout: 30 seconds
Interval: 40 seconds
Path: / (default)
```

#### Register Targets
- Select application instance
- Add as pending target
- Health checks will validate instance availability

### 4. Configure Load Balancer Listener
```
Protocol: HTTP
Port: 80
Target Group: app-target-group
```

### 5. Create Launch Template

#### Template Configuration
```
Name: app-launch-template
Description: Web server for employee directory application
Auto Scaling Guidance: Enable for EC2 Auto Scaling
```

#### Instance Configuration
- **AMI**: Use application AMI
- **Instance Type**: Match existing instance
- **Key Pair**: Use existing key pair
- **Security Groups**: Application security group
- **IAM Role**: Instance role for S3/DynamoDB access
- **User Data**: Application bootstrap script

### 6. Create Auto Scaling Group

#### Group Configuration
```
Name: app-auto-scaling-group
Launch Template: app-launch-template
VPC: app-vpc
Subnets: Private subnets across multiple AZs
```

#### Capacity Settings
```
Minimum: 2 instances
Desired: 2 instances
Maximum: 4 instances
```

#### Load Balancer Integration
```
Target Group: app-target-group
Health Check Type: ELB
Health Check Grace Period: 300 seconds
```

### 7. Configure Scaling Policies

#### Target Tracking Policy
```
Metric: Average CPU Utilization
Target Value: 70%
Scale-out Cooldown: 300 seconds
Scale-in Cooldown: 300 seconds
```

## Verification Steps

### 1. Test Load Balancer
- Copy ALB DNS name
- Access application via load balancer endpoint
- Verify application functionality and data persistence

### 2. Test Auto Scaling
- Monitor CloudWatch metrics
- Verify instances launch in multiple AZs
- Test scaling policies with load testing

### 3. Test High Availability
- Terminate one instance manually
- Verify Auto Scaling replaces instance
- Confirm no service interruption

## Key Benefits Achieved
- **High Availability**: Multi-AZ deployment with automatic failover
- **Scalability**: Automatic capacity adjustment based on demand
- **Cost Optimization**: Pay only for needed capacity
- **Health Monitoring**: Automatic replacement of unhealthy instances
- **Load Distribution**: Even traffic distribution across instances

## Monitoring and Maintenance
- Monitor CloudWatch metrics for performance
- Review Auto Scaling activities
- Update launch template for application changes
- Adjust scaling policies based on usage patterns