# Introduction to Networking

## What is Networking?

**Networking:** How computers connect and communicate with each other worldwide

## AWS Networking Context

### Default VPC
- AWS creates default VPCs in every region
- Provides easy EC2 instance launch with internet access
- **Warning:** Resources are publicly accessible
- Good for quick testing, not production

### Custom VPC
- More secure than default VPC
- Granular internet access control
- Required for production workloads

## Networking Basics

### IP Addresses
**Purpose:** Unique identifier for each computer (like mailing addresses)

### IPv4 Format
- **Binary:** 32 bits (0s and 1s)
- **Decimal:** Four 8-bit groups separated by periods
- **Example:** 192.168.1.30

### CIDR Notation
**Format:** `IP_ADDRESS/NUMBER`
**Example:** `192.168.1.0/24`

#### How CIDR Works
- Number after `/` = fixed bits
- Remaining bits = flexible (available addresses)
- `192.168.1.0/24` = first 24 bits fixed, last 8 flexible
- 8 flexible bits = 2^8 = 256 addresses

#### CIDR Examples
| CIDR | Fixed Bits | Flexible Bits | Available IPs |
|------|------------|---------------|---------------|
| /28 | 28 | 4 | 16 |
| /24 | 24 | 8 | 256 |
| /16 | 16 | 16 | 65,536 |

### AWS CIDR Limits
- **Smallest:** /28 (16 IP addresses)
- **Largest:** /16 (65,536 IP addresses)

## Key Concepts

**Routing:** How messages are delivered between computers  
**Octets:** 8-bit groups in IPv4 addresses  
**Higher /number = Smaller network range**

## Important Notes

- Networking is fundamental to most AWS architectures
- Lambda functions may not need VPC networking
- Focus on EC2-related networking concepts