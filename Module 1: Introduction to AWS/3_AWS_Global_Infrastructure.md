# AWS Global Infrastructure

## Overview
AWS Global Infrastructure consists of Regions, Availability Zones, and Edge Locations in a nested, redundant structure.

## Regions

### Definition
- Geographic locations worldwide where AWS hosts data centers
- 37 geographic Regions with 117 Availability Zones globally
- Named after their location (e.g., Northern Virginia, Oregon)
- Span Asia Pacific, China, Europe, Middle East, North America, South America

### Region Codes
- **us-east-1**: N. Virginia (first eastern US Region)
- **ap-northeast-1**: Tokyo (first northeast Asia Pacific Region)

### Choosing the Right Region - 4 Key Factors

#### 1. Latency
- Choose Region close to user base
- Critical for synchronous applications (gaming, telephony, WebSockets, IoT)
- Also affects asynchronous workloads (ecommerce)

#### 2. Pricing
- Varies by Region due to local economy factors
- Internet connectivity, equipment costs, customs, real estate
- No flat worldwide rate

#### 3. Service Availability
- Not all services available in all Regions
- Check AWS documentation for service availability table
- New services don't roll out to all Regions immediately

#### 4. Data Compliance
- Regulations may require data storage in specific territories
- Choose Region meeting compliance requirements

## Availability Zones (AZs)

### Structure
- Cluster of AZs inside each Region
- One or more data centers per AZ
- Redundant power, networking, connectivity
- Connected via high-speed, low-latency links
- Discrete facilities in undisclosed locations

### Naming Convention
- Region code + letter (e.g., us-east-1a, sa-east-1b)
- Example: us-east-1c = Availability Zone c in N. Virginia Region

## Service Scope Levels

### Region-Scoped Services
- Select Region only
- AWS automatically handles durability and availability
- Built-in resiliency

### Availability Zone-Scoped Services
- Must specify individual AZ
- User responsible for durability and high availability

## Best Practices for Resiliency

### High Availability Strategy
- Use Region-scoped managed services when possible
- Replicate workloads across multiple AZs
- Minimum: Use 2 Availability Zones
- If one AZ fails, traffic shifts to backup AZ

## Edge Locations

### Purpose
- Cache content closer to end users
- Reduce latency globally
- 400+ edge locations worldwide

### How It Works
**Without Caching:**
- All requests go to origin Region
- High latency for distant users

**With Edge Caching:**
- Content cached at nearest edge location
- Requests served from closest cache
- Significantly reduced latency

### Amazon CloudFront
- Content delivery through worldwide edge network
- Routes requests to lowest latency location
- Uses AWS backbone network for optimal performance

## Infrastructure Hierarchy
```
Global Infrastructure
├── Regions (37)
│   ├── Availability Zones (117 total)
│   │   └── Data Centers (multiple per AZ)
└── Edge Locations (400+)
```