# Amazon RDS

## What is Amazon RDS?

**Amazon RDS:** Managed relational database service that handles infrastructure tasks (provisioning, patching, scaling, restoring) so you can focus on application development.

## Supported Database Engines

### Commercial
- Oracle
- SQL Server

### Open Source
- MySQL
- PostgreSQL
- MariaDB

### Cloud Native
- Amazon Aurora

## RDS Components

### Database Instance
- **Compute:** DB instance running the database engine
- **Underlying:** Managed EC2 instance (accessed via RDS console)
- **Configuration:** Instance type and size affect processing power and memory
- **Multiple databases:** Single instance can host multiple databases

### Storage Types
| Type | Description | Use Case |
|------|-------------|----------|
| **General Purpose SSD (gp2/gp3)** | Balanced performance | Most workloads |
| **Provisioned IOPS SSD (io1)** | High performance | I/O intensive applications |
| **Magnetic (standard)** | Lower cost | Light workloads |

### Aurora Storage
- **Cluster volumes:** Single virtual volume using SSDs
- **Replication:** Data copied across 3 AZs automatically
- **Local storage:** For temporary, non-persistent files

## Network Configuration

### VPC Placement
- **DB Subnet Group:** Minimum 2 AZs required
- **Private subnets:** No internet gateway route
- **Access control:** Network ACLs and security groups
- **Backend only:** Database accessible only by application servers

## Backup Options

### Automated Backups
- **Default:** Enabled automatically
- **Scope:** Entire DB instance + transaction logs
- **Retention:** 0-35 days (0 = disabled)
- **Backup window:** Set during low-activity periods
- **Point-in-time recovery:** Restore to specific timestamp

### Manual Snapshots
- **Retention:** Until manually deleted
- **Use case:** Long-term retention (>35 days), compliance
- **Management:** Initiated manually via RDS console
- **Restoration:** Creates new DB instance from snapshot

## High Availability: Multi-AZ

### Architecture
- **Primary:** Active database in one AZ
- **Standby:** Synchronous replica in different AZ
- **Replication:** Automatic synchronous data copying
- **Access:** Applications only query primary database

### Failover Process
1. **Detection:** Primary database connectivity loss
2. **Automatic failover:** Standby promoted to primary
3. **DNS redirect:** Traffic routed to new primary
4. **Standby recreation:** New standby established

### Benefits
- **High availability:** Automatic failover capability
- **Data protection:** Synchronous replication
- **Minimal downtime:** DNS-based failover

## Security Features

### Access Control
- **IAM policies:** Control who can manage RDS resources
- **Security groups:** Control IP/instance access to databases
- **Network ACLs:** Additional network-level filtering

### Data Protection
- **Encryption at rest:** Secure DB instances and snapshots
- **Encryption in transit:** SSL/TLS connections supported
- **Engine support:** MySQL, MariaDB, PostgreSQL, Oracle, SQL Server

## Best Practices

- **Use both backup types:** Automated + manual snapshots
- **Multi-AZ deployment:** For production workloads
- **Private subnets:** Keep databases isolated from internet
- **Security groups:** Restrict access to application tier only