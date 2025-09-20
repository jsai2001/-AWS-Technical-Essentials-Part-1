# Introduction to Serverless

## What is Serverless?

**Serverless:** Computing model where you cannot see or access underlying infrastructure. AWS manages provisioning, scaling, fault tolerance, and maintenance.

## Four Key Aspects of Serverless

1. **No servers to provision or manage**
2. **Scales automatically with usage**
3. **Pay only for what you use (no idle costs)**
4. **Built-in availability and fault tolerance**

## Traditional vs Serverless Responsibility

### EC2 (Traditional)
**AWS:** Physical hardware  
**You:** Guest OS, patching, networking, security, scaling

### Containers on EC2
**AWS:** Container management, cluster orchestration  
**You:** EC2 instances, OS maintenance

### Serverless
**AWS:** Infrastructure, OS, scaling, availability  
**You:** Application code, data encryption, access management

## Benefits of Serverless

- **Focus on business logic** - Not infrastructure management
- **Reduced operational overhead** - No scaling or fault tolerance design needed
- **Convenience over control** - AWS handles undifferentiated heavy lifting
- **Faster development** - Less time on infrastructure, more on features

## AWS Serverless Spectrum

**Control ←→ Convenience**

- **High Control:** EC2 instances
- **Medium Control:** Containers on EC2
- **High Convenience:** AWS Lambda, AWS Fargate

## Key Serverless Services

- **AWS Lambda** - Serverless compute functions
- **AWS Fargate** - Serverless containers