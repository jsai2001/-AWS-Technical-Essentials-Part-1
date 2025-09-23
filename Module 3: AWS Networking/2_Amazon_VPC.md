# Amazon VPC

## What is a VPC?

**VPC (Virtual Private Cloud):** Isolated network in AWS Cloud, similar to traditional data center network

## VPC Configuration

### Required Settings
1. **Name** - VPC identifier
2. **Region** - VPC spans all AZs in selected region
3. **IP Range** - CIDR notation (e.g., 10.0.0.0/16)

### CIDR Limits
- **Primary CIDR:** 1 required
- **Secondary CIDRs:** Up to 4 additional
- **Size range:** /28 to /16

## Subnets

**Subnet:** Smaller network inside VPC (like VLANs)

### Subnet Types
- **Public Subnet** - Resources accessible from internet
- **Private Subnet** - Internal resources only

### Subnet Configuration
- **VPC** - Parent VPC to create subnet in
- **Availability Zone** - Specific AZ for subnet
- **CIDR Block** - Must be subset of VPC CIDR

### Example Setup
```
VPC: 10.1.0.0/16
├── Public Subnet 1: 10.1.1.0/24 (AZ-A)
├── Private Subnet 1: 10.1.3.0/24 (AZ-A)
├── Public Subnet 2: 10.1.2.0/24 (AZ-B)
└── Private Subnet 2: 10.1.4.0/24 (AZ-B)
```

## High Availability

### Best Practice
- **Minimum 2 AZs** - Deploy resources across multiple zones
- **Redundant subnets** - Create subnets in each AZ
- **Fault tolerance** - If one AZ fails, others continue

## Reserved IP Addresses

AWS reserves **5 IP addresses** per subnet:
- Network address
- VPC router
- DNS server
- Future use
- Broadcast address

### Impact on Capacity
- /24 subnet = 256 total IPs
- 256 - 5 reserved = **251 usable IPs**

## Gateways

### Internet Gateway
- **Purpose:** Connect VPC to internet
- **Analogy:** Like a modem for your VPC
- **Properties:** Highly available, scalable
- **Setup:** Create → Attach to VPC

### Virtual Private Gateway (VGW)
- **Purpose:** VPN connection to on-premises
- **Use case:** Private network connectivity
- **Security:** Encrypted VPN tunnel
- **Requires:** Customer gateway on premises side

### AWS Direct Connect
- **Purpose:** Dedicated physical connection
- **Benefits:** Private, consistent network performance
- **Connection:** Fiber-optic cable to AWS location
- **Traffic:** Never touches public internet

## Common VPC Design

**Recommended starting point:**
- VPC: /16 CIDR (65,536 IPs)
- Subnets: /24 CIDR (256 IPs each)
- Multiple AZs for high availability