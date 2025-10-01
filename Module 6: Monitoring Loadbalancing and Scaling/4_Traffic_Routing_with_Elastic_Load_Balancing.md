# Traffic Routing with Elastic Load Balancing

## Overview
Elastic Load Balancing (ELB) distributes incoming application traffic across multiple targets (EC2 instances, containers, IP addresses, Lambda functions) using algorithms like round robin.

## ELB Key Features
- **Managed Service**: No need to manage or operate load balancer infrastructure
- **Hybrid Mode**: Load balance to both AWS and on-premises servers via IP addresses
- **High Availability**: Deploy targets across multiple Availability Zones
- **Auto Scaling**: Automatically scales to meet incoming traffic demand

## Health Checks
ELB supports two health check types:
- **TCP Connection**: Establishes connection to backend instance
- **HTTP/HTTPS Request**: Makes request to specified webpage and validates response code

### Best Practice
Create dedicated monitoring endpoint (e.g., `/monitor`) that validates:
- Database connectivity
- Amazon S3 access
- Application dependencies

## ALB Components
- **Listeners**: Check for connection requests using configured protocol and port
- **Rules**: Define how to route requests to targets
- **Target Groups**: Route requests to registered targets using specified protocol and port

## Load Balancer Types

### Application Load Balancer (ALB)
**Layer 7 (HTTP/HTTPS)**

| Feature | Description |
|---------|-------------|
| Routing | Based on URL path, host, headers, method, source IP |
| Direct Response | Fixed responses, redirects (HTTP to HTTPS) |
| TLS Offloading | SSL certificate via IAM/ACM |
| Authentication | OIDC, SAML, LDAP, Active Directory |
| Security | Security groups for IP filtering |
| Sticky Sessions | Route requests to same backend server |

### Network Load Balancer (NLB)
**Layer 4 (TCP/UDP)**

| Feature | Description |
|---------|-------------|
| Performance | Ultra-low latency for latency-sensitive applications |
| IP Preservation | Maintains client-side source IP address |
| Static IP | Automatic static IP per Availability Zone |
| Custom IP | Assign custom fixed IP per Availability Zone |
| Routing | Same client to same target |

### Gateway Load Balancer (GLB)
**Layer 3 Gateway + Layer 4 Load Balancing**

| Feature | Description |
|---------|-------------|
| Third-party Appliances | Deploy firewalls, IDS/IPS, deep packet inspection |
| High Availability | Routes traffic through healthy virtual appliances |
| Monitoring | CloudWatch metrics integration |
| Marketplace | Deploy appliances from AWS Marketplace |
| Private Network | Connects IGW, VPCs, network resources |

## ELB Type Comparison

| Feature | ALB | NLB | GLB |
|---------|-----|-----|-----|
| **OSI Layer** | Layer 7 | Layer 4 | Layer 3/4 |
| **Target Types** | IP, Instance, Lambda | IP, Instance, ALB | IP, Instance |
| **Protocols** | HTTP, HTTPS | TCP, UDP, TLS | IP |
| **Static IP** | No | Yes | No |
| **Source IP Preservation** | No | Yes | Yes |
| **Fixed Response** | Yes | No | No |
| **User Authentication** | Yes | No | No |

## Integration with Auto Scaling
- ELB informs Auto Scaling of unhealthy instances
- **Connection Draining**: Prevents termination until existing connections complete
- Auto Scaling replaces failed instances automatically