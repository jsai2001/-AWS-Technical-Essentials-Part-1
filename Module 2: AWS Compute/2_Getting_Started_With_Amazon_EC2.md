# Getting Started with Amazon EC2

## Amazon Machine Images (AMIs)

**AMI:** Template containing OS, software, and configurations to launch EC2 instances

### AMI Sources
- **Quick Start** - AWS-created common AMIs
- **AWS Marketplace** - Third-party commercial/open-source
- **My AMIs** - Custom AMIs from your instances
- **Community AMIs** - User community contributions
- **Custom Image** - Built with EC2 Image Builder

### AMI Benefits
- **Reusable** - Launch multiple identical instances
- **Consistent** - Same configurations across instances
- **Portable** - Copy between regions (unique AMI IDs per region)

## EC2 Instance Types

Format: `[family][generation][attributes].[size]`  
Example: `c5n.xlarge`
- `c` = Compute optimized family
- `5` = 5th generation
- `n` = NVMe storage
- `xlarge` = Instance size

### Instance Families

| Family | Optimized For | Use Cases |
|--------|---------------|-----------|
| **General Purpose** | Balanced resources | Web servers, code repositories |
| **Compute Optimized** | High-performance CPU | Batch processing, HPC, gaming servers |
| **Memory Optimized** | Large datasets in memory | Databases, in-memory caches, analytics |
| **Accelerated Computing** | Hardware accelerators | Machine learning, graphics processing |
| **Storage Optimized** | High I/O operations | NoSQL databases, data warehousing |
| **HPC Optimized** | HPC workloads | Complex simulations, deep learning |

## EC2 Configuration

### Key Components
- **vCPUs** - Virtual processors
- **Memory** - RAM capacity
- **Network** - Bandwidth and performance
- **Storage** - Instance store or EBS volumes
- **GPUs** - Graphics processing (select instances)

### Instance Placement
- **Default VPC** - Public, internet-accessible (not for production)
- **Custom VPC** - Private, controlled access (recommended)
- **Availability Zone** - Physical location within region

## High Availability Architecture

### Best Practices
- Use **multiple instances** instead of single large instance
- Deploy across **multiple Availability Zones**
- **Minimum 2 instances** in 2 separate AZs

### Benefits
- **Fault tolerance** - Single instance failure doesn't affect entire application
- **Better performance** - Distributed load
- **Cost optimization** - Smaller instances often more cost-effective