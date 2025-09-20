# Compute as a Service

## Three Types of Compute Options

1. **Virtual Machines (VMs)** - Traditional server virtualization
2. **Container Services** - Containerized applications
3. **Serverless** - Event-driven, managed compute

## On-Premises vs Cloud Compute

### On-Premises Challenges
- Research and purchase hardware upfront
- Wait weeks/months for delivery
- Install, rack, and wire servers
- Manage data center space
- Stuck with capacity whether used or not

### AWS Compute Benefits
- Pre-built, secured data centers
- Servers ready to use immediately
- Pay for what you use
- Scale up/down on demand

## Servers and Client-Server Model

**Server:** Computer handling HTTP requests and sending responses  
**Client:** Person or computer sending requests

### Common HTTP Servers
- **Windows:** Internet Information Services (IIS)
- **Linux:** Apache HTTP Server, Nginx, Apache Tomcat

## Virtual Machines on AWS

### Amazon EC2 (Elastic Compute Cloud)
- Web service providing resizable compute capacity
- Provisions virtual servers called EC2 instances
- AWS manages host machines and hypervisor layer
- AWS installs guest operating system

### How It Works
- **Hypervisor:** Software sharing physical hardware across VMs
- **Host Machine:** Physical server managed by AWS
- **Guest OS:** Virtual machine operating system
- **EC2 Instance:** Individual virtual server

## Key Concept

EC2 is foundational to understanding AWS compute services. Many other AWS services use EC2 or virtualization concepts underneath.