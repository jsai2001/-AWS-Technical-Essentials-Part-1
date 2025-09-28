# Block Storage with Amazon EC2 Instance Store and Amazon EBS

## Two Types of Block Storage

### EC2 Instance Store
- **Type:** Ephemeral (temporary) storage
- **Location:** Physically attached to host computer
- **Lifecycle:** Tied to EC2 instance (deleted when instance terminates)
- **Performance:** High-speed local storage

**Use Cases:**
- Hadoop clusters and distributed applications
- Temporary data (buffers, caches, scratch data)
- Applications with built-in data replication

### Amazon EBS (Elastic Block Store)
- **Type:** Persistent storage
- **Location:** Network-attached storage
- **Lifecycle:** Independent of EC2 instance
- **Performance:** Consistent, scalable

## EBS Characteristics

### Similar to External Drive
- **Detachable:** Move between EC2 instances (same AZ)
- **Distinct:** Survives instance termination
- **Size-limited:** Maximum 64 TiB per volume
- **1-to-1 connection:** Usually one volume per instance*

*Multi-attach available for io1/io2 volumes in same AZ

## EBS Volume Types

### SSD Volumes (Transactional Workloads)

| Type | Description | Size | Max IOPS | Max Throughput | Multi-attach |
|------|-------------|------|----------|----------------|--------------|
| **gp3** | General Purpose | 1 GiB-16 TiB | 16,000 | 1,000 MiB/s | No |
| **gp2** | General Purpose | 1 GiB-16 TiB | 16,000 | 250 MiB/s | No |
| **io2** | Provisioned IOPS | 4 GiB-16 TiB | 64,000 | 1,000 MiB/s | Yes |
| **io2 Block Express** | High Performance | 4 GiB-64 TiB | 256,000 | 4,000 MiB/s | Yes |

### HDD Volumes (Throughput Workloads)

| Type | Description | Size | Max IOPS | Max Throughput |
|------|-------------|------|----------|----------------|
| **st1** | Throughput Optimized | 125 GiB-16 TiB | 500 | 500 MiB/s |
| **sc1** | Cold HDD | 125 GiB-16 TiB | 250 | 250 MiB/s |

## EBS Scaling Options

1. **Increase Volume Size** - Up to maximum limits (64 TiB)
2. **Attach Multiple Volumes** - Add additional EBS volumes

## EBS Use Cases

- **Operating Systems** - Boot/root volumes for AMIs
- **Databases** - Persistent storage with consistent performance
- **Enterprise Applications** - High availability, business-critical data
- **Big Data Analytics** - Resizable clusters with data persistence

## EBS Benefits

- **High Availability** - Automatically replicated within AZ
- **Persistent** - Data survives instance termination
- **Encrypted** - Optional encryption for all volume types
- **Flexible** - Modify size, type, IOPS without stopping instance
- **Backup** - Snapshot capability for data protection

## EBS Snapshots

### Overview
- **Incremental backups** stored in Amazon S3
- Only changed blocks saved after first snapshot
- **Cross-AZ replication** for redundancy
- Managed through EC2 console

### Benefits
- Create new volumes from snapshots
- Copy volumes across Availability Zones
- Point-in-time recovery capability
- Cost-effective (only pay for changed data)