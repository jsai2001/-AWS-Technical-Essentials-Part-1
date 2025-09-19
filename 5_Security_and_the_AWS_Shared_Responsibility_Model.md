# AWS Shared Responsibility Model

Security and compliance are shared between AWS and customers.

## Core Concept

**AWS:** Security **OF** the cloud  
**Customer:** Security **IN** the cloud

## AWS Responsibilities (Security OF the Cloud)

- **Physical infrastructure** - Data centers, buildings, security guards
- **Global backbone** - Private fiber cables connecting regions
- **Hardware & software** - Host OS, hypervisor, networking components
- **AWS services infrastructure** - Compute, database, storage platforms

## Customer Responsibilities (Security IN the Cloud)

- **Data protection** - Encryption at rest and in transit
- **Access control** - User permissions and authentication
- **Operating system** - Patching and updates (for EC2)
- **Network security** - Firewalls and network configuration
- **Application security** - Code and application-level controls

## Service Categories

### Infrastructure Services (e.g., EC2)
| AWS | Customer |
|-----|----------|
| Physical infrastructure | Operating system |
| Host OS & hypervisor | Application platform |
| Networking components | Data encryption |
| | Access control |

### Abstracted Services (e.g., S3)
| AWS | Customer |
|-----|----------|
| Infrastructure layer | Customer data |
| Operating system | Data encryption |
| Platform management | Network firewalls |
| Server-side encryption | Backups |

## Key Customer Responsibilities

- **Data sovereignty** - Choose appropriate regions
- **Data protection** - Implement encryption and backups  
- **Access control** - Manage who accesses what resources
- **Compliance** - Meet industry and regulatory requirements

## Remember

- You **own your data** - ultimate responsibility for data security
- Responsibility varies by service type
- AWS provides security tools - you must configure and use them