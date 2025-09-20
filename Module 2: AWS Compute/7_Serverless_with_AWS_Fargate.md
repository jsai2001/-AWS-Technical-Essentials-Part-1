# Serverless with AWS Fargate

## What is AWS Fargate?

**AWS Fargate:** Serverless compute platform for containers that works with ECS and EKS

## Key Benefits

- **No infrastructure management** - No provisioning, patching, or scaling
- **Built-in scaling and fault tolerance**
- **Pay-as-you-go** - Only pay for vCPU, memory, and storage consumed
- **Workload isolation** - Improved security by design

## How Fargate Works

### Container Orchestration Options
- **Amazon ECS** - AWS native orchestration
- **Amazon EKS** - Managed Kubernetes

### Deployment Process
1. Build container images
2. Push to Amazon ECR (Elastic Container Registry)
3. Define memory and compute resources for tasks/pods
4. Run containers on Fargate platform

## Fargate vs EC2 for Containers

| Aspect | EC2 | Fargate |
|--------|-----|---------|
| **Infrastructure** | Manage instances | Serverless |
| **Scaling** | Manual/Auto Scaling Groups | Automatic |
| **Patching** | Your responsibility | AWS managed |
| **Control** | Full OS access | Container-level only |
| **Pricing** | Instance hours | Resource consumption |

## Pricing Options

- **On-Demand** - Pay for resources used
- **Spot** - Up to 70% savings for fault-tolerant workloads
- **Savings Plans** - Commitment-based discounts

## Common Use Cases

- **Microservices** - Independent, scalable services
- **Batch processing** - Event-driven workloads
- **Machine learning** - Training and inference jobs
- **Application migration** - Lift-and-shift to containers

## Integration Features

- **IAM** - Native identity and access management
- **VPC** - Launch containers inside your network
- **ECS/EKS APIs** - Same concepts and integrations