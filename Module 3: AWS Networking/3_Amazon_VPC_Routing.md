# Amazon VPC Routing

## What are Route Tables?

**Route Table:** Set of rules (routes) that determine where network traffic is directed

## Main Route Table

### Default Behavior
- AWS creates main route table for every VPC
- Applied to entire VPC by default
- Contains local route for VPC CIDR (enables subnet-to-subnet communication)

### Main Route Table Rules
- Cannot be deleted
- Cannot set gateway route table as main
- Can be replaced with custom route table
- Can add/remove/modify routes
- Subnets use main table unless explicitly associated with custom table

## Custom Route Tables

### Purpose
- Provide different routing rules per subnet
- Control public vs private access
- Better security through explicit associations

### Creating Custom Route Table
1. Create route table in VPC
2. Add routes (local route included automatically)
3. Associate with specific subnets

## Public vs Private Subnets

**Key Concept:** Route table determines subnet accessibility, not the subnet itself

### Public Subnet Route Table
```
Destination: 0.0.0.0/0 → Target: Internet Gateway
Destination: 10.0.0.0/16 → Target: Local
```

### Private Subnet Route Table
```
Destination: 10.0.0.0/16 → Target: Local
(No internet gateway route)
```

## Route Table Configuration Example

### Public Route Table Setup
1. **Create:** `app-routetable-public`
2. **Add Route:** 
   - Destination: `0.0.0.0/0` (anywhere)
   - Target: Internet Gateway
3. **Associate:** Public subnets only

### Private Route Table Setup
1. **Create:** `app-routetable-private`
2. **Routes:** Local only (no IGW route)
3. **Associate:** Private subnets only

## Best Practices

- **Explicit associations** - Associate each subnet with custom route table
- **Leave main table default** - Keep main route table in original state
- **Separate public/private** - Different route tables for different access needs
- **Security principle** - Only add routes that are necessary

## Common Routes

| Destination | Target | Purpose |
|-------------|--------|---------|
| `10.0.0.0/16` | Local | VPC internal traffic |
| `0.0.0.0/0` | Internet Gateway | Internet access |
| `10.1.0.0/16` | VPN Gateway | On-premises access |