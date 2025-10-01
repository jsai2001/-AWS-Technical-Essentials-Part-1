# Amazon EC2 Auto Scaling

## Overview
Amazon EC2 Auto Scaling automatically adds and removes EC2 instances based on CloudWatch metrics to maintain steady performance at lowest cost. Provides pay-as-you-go scaling versus traditional over-provisioning.

## Key Features
- **Dynamic Scaling**: Automatically scales in/out based on demand
- **Scheduled Scaling**: Scales based on user-defined schedules
- **Health Replacement**: Automatically replaces unhealthy instances
- **Machine Learning**: Uses ML to optimize instance scheduling
- **Multi-Model Support**: Supports multiple purchase models, instance types, and AZs
- **Integrated Service**: Included with Amazon EC2

## ELB Integration
- ELB receives notifications when instances are added/removed
- Health checks validate new instances before receiving traffic
- Seamless integration for high availability

## Auto Scaling Components

### 1. Launch Template/Configuration
**Defines: Which resources to scale**

#### Launch Template (Recommended)
- Stores EC2 instance configuration (AMI ID, instance type, security groups, EBS volumes)
- Supports versioning for rollback capability
- Can be created from:
  - Existing EC2 instance
  - Existing template/previous version
  - From scratch

#### Launch Configuration (Legacy)
- Similar to launch template but without versioning
- Cannot use existing instances as templates
- AWS recommends launch templates instead

### 2. Auto Scaling Groups
**Defines: Where to deploy resources**

| Configuration | Description |
|---------------|-------------|
| **VPC/Subnets** | Specify deployment locations across AZs |
| **Purchase Options** | On-Demand, Spot, or combination |
| **Capacity Settings** | Minimum, desired, maximum instances |

#### Capacity Settings
- **Minimum**: Lowest number of instances (always running)
- **Desired**: Target number of instances (default state)
- **Maximum**: Upper limit for scaling out

### 3. Scaling Policies
**Defines: When to add/remove resources**

Uses CloudWatch metrics and alarms to trigger scaling actions.

## Scaling Policy Types

### Simple Scaling Policy
| Feature | Description |
|---------|-------------|
| **Trigger** | Single CloudWatch alarm |
| **Action** | Add/remove specific number or percentage of instances |
| **Cooldown** | Prevents additional actions during instance startup |
| **Limitation** | Cannot handle multiple alarm thresholds |

### Step Scaling Policy
| Feature | Description |
|---------|-------------|
| **Multiple Steps** | Different actions for different alarm thresholds |
| **Example** | +2 instances at 85% CPU, +4 instances at 95% CPU |
| **Concurrent Actions** | Responds to alarms during ongoing scaling |
| **Flexibility** | More granular control than simple scaling |

### Target Tracking Scaling Policy
| Feature | Description |
|---------|-------------|
| **Automatic Setup** | Creates required CloudWatch alarms automatically |
| **Target Metrics** | Average CPU, network utilization, request count |
| **Simplicity** | Only requires target value specification |
| **Recommended** | Best for common scaling scenarios |

## Best Practices
- Use launch templates over launch configurations
- Deploy across multiple Availability Zones
- Configure appropriate health checks
- Set realistic cooldown periods
- Use target tracking for common metrics
- Combine with ELB for high availability