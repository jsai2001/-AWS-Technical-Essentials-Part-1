# File Storage with Amazon EFS and Amazon FSx

## Amazon EFS (Elastic File System)

### Overview
- **Fully managed** NFS file system
- **Auto-scaling** - Grows/shrinks automatically
- **No provisioning** - Set-and-forget storage
- **Multi-instance access** - Thousands of concurrent connections

### Storage Classes
| Class | Availability | Use Case |
|-------|--------------|----------|
| **EFS Standard** | Multi-AZ | Frequently accessed data |
| **EFS Standard-IA** | Multi-AZ | Infrequently accessed data |
| **EFS One Zone** | Single AZ | Cost-optimized frequent access |
| **EFS One Zone-IA** | Single AZ | Cost-optimized infrequent access |

### Key Features
- Pay only for storage used
- Consistent performance across instances
- Works with AWS compute and on-premises
- Simple web interface management

## Amazon FSx

### Overview
Fully managed service offering four high-performance file systems:

### FSx for NetApp ONTAP
- **Purpose:** Drop-in replacement for on-premises NetApp
- **Access:** Linux, Windows, macOS
- **Features:** Rich data management, flexible shared storage
- **Best for:** Existing ONTAP deployments

### FSx for OpenZFS
- **Purpose:** Linux-based file server migration
- **Performance:** Low latency, small-file workloads
- **Features:** Snapshots, cloning, NAS capabilities
- **Best for:** ZFS migrations without code changes

### FSx for Windows File Server
- **Purpose:** Native Windows file systems
- **Protocol:** SMB (Service Message Block)
- **Features:** Drop-in replacement for Windows file servers
- **Best for:** Windows applications and environments

### FSx for Lustre
- **Purpose:** High-performance computing workloads
- **Performance:** Up to 1+ TB/s throughput, millions of IOPS
- **Integration:** Links to S3 and on-premises data stores
- **Best for:** Applications requiring fast storage

## Service Comparison

| Service | File System | Performance | Use Case |
|---------|-------------|-------------|----------|
| **EFS** | NFS | Standard | General-purpose, multi-instance |
| **FSx ONTAP** | NetApp | High | Enterprise data management |
| **FSx OpenZFS** | ZFS | High | Linux workloads, snapshots |
| **FSx Windows** | NTFS | High | Windows environments |
| **FSx Lustre** | Lustre | Highest | HPC, big data analytics |