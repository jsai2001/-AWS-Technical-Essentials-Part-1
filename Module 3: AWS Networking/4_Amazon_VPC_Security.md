# Amazon VPC Security

## Two Layers of Security

1. **Network ACLs** - Subnet-level firewall
2. **Security Groups** - Instance-level firewall

## Network Access Control Lists (ACLs)

### Overview
- **Level:** Subnet firewall
- **Default:** Allow all inbound/outbound traffic
- **Behavior:** Stateless (must configure both inbound and outbound)
- **Rules:** Allow and deny rules supported

### Default Network ACL
| Direction | Rule | Traffic | Action |
|-----------|------|---------|--------|
| Inbound | 100 | All IPv4 | ALLOW |
| Inbound | * | All IPv4 | DENY |
| Outbound | 100 | All IPv4 | ALLOW |
| Outbound | * | All IPv4 | DENY |

### Custom Network ACL Example
| Direction | Port | Protocol | Source/Dest | Action | Purpose |
|-----------|------|----------|-------------|--------|---------|
| Inbound | 443 | TCP | 0.0.0.0/0 | ALLOW | HTTPS traffic |
| Inbound | 3389 | TCP | 192.0.2.0/24 | ALLOW | RDP from home |
| Outbound | 1025-65535 | TCP | 0.0.0.0/0 | ALLOW | Response traffic |

### Key Points
- **Stateless:** Must configure both directions
- **Ephemeral ports:** Need outbound range for responses
- **Rule evaluation:** Processed in order by rule number

## Security Groups

### Overview
- **Level:** EC2 instance firewall
- **Default:** Block all inbound, allow all outbound
- **Behavior:** Stateful (remembers connections)
- **Rules:** Allow rules only (no deny rules)

### Default Behavior
- **Inbound:** All traffic blocked
- **Outbound:** All traffic allowed
- **Stateful:** Response traffic automatically allowed

### Web Server Security Group Example
| Direction | Type | Protocol | Port | Source |
|-----------|------|----------|------|--------|
| Inbound | HTTP | TCP | 80 | 0.0.0.0/0 |
| Inbound | HTTPS | TCP | 443 | 0.0.0.0/0 |

## Network ACLs vs Security Groups

| Aspect | Network ACLs | Security Groups |
|--------|--------------|-----------------|
| **Level** | Subnet | Instance |
| **Default** | Allow all | Block inbound |
| **State** | Stateless | Stateful |
| **Rules** | Allow + Deny | Allow only |
| **Processing** | Rule order matters | All rules evaluated |

## Multi-Tier Architecture Security

### Common Pattern
- **Web Tier:** Internet → HTTPS (443)
- **App Tier:** Web → HTTP (80)
- **DB Tier:** App → MySQL (3306)

### Benefits
- **Isolation:** Each tier has specific access rules
- **Flexibility:** Not tied to network configuration
- **Security:** Principle of least privilege

## Best Practices

- **Default approach:** Use security groups primarily, leave ACLs default
- **Defense in depth:** Use both layers for sensitive workloads
- **Least privilege:** Only open required ports
- **Specific sources:** Avoid 0.0.0.0/0 when possible