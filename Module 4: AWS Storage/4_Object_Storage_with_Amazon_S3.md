# Object Storage with Amazon S3

## S3 Bucket Policies

### Purpose
Specify allowed/denied actions on S3 buckets using JSON policies

### Use Cases
- **Cross-account access** without IAM roles
- **Large policies** that exceed IAM policy size limits
- **Bucket-level permissions** for specific scenarios

## S3 Encryption

- **In transit** - Data encrypted while traveling to/from S3
- **At rest** - All objects automatically encrypted on upload
- **Default** - Server-side encryption with S3-managed keys (no additional cost)

## S3 Storage Classes

| Class | Access Pattern | Retrieval Time | Use Case |
|-------|----------------|----------------|----------|
| **S3 Standard** | Frequent | Immediate | General-purpose, dynamic websites |
| **S3 Intelligent-Tiering** | Unknown/changing | Automatic | Unpredictable access patterns |
| **S3 Standard-IA** | Infrequent | Immediate | Long-term backups, disaster recovery |
| **S3 One Zone-IA** | Infrequent | Immediate | Secondary backups, recreatable data |
| **S3 Glacier Instant Retrieval** | Rare | Milliseconds | Archive with instant access |
| **S3 Glacier Flexible Retrieval** | 1-2 times/year | 1-5 minutes | Backup, disaster recovery |
| **S3 Glacier Deep Archive** | Once/twice year | 12 hours | Long-term retention, compliance |
| **S3 Outposts** | On-premises | Immediate | Local data residency requirements |

## S3 Versioning

### Purpose
Keep multiple versions of objects in same bucket

### Benefits
- **Prevent overwrites** - Preserve original objects
- **Accidental deletion protection** - Objects marked, not deleted
- **Version history** - Access previous object versions
- **Application failure recovery** - Restore from earlier versions

### Versioning States
- **Unversioned** (default) - No version IDs assigned
- **Versioning-enabled** - All objects get version IDs (cannot revert)
- **Versioning-suspended** - New objects unversioned, existing keep versions

### Example
```
employeephoto.jpg (version 111111)
employeephoto.jpg (version 121212)
```

## Lifecycle Management

### Automation Types
1. **Transition Actions** - Move objects between storage classes
2. **Expiration Actions** - Permanently delete objects

### Example Rules
- Transition to Standard-IA after 30 days
- Archive to Glacier Deep Archive after 1 year
- Delete after regulatory retention period

### Use Cases
- **Periodic logs** - Delete after week/month
- **Changing access patterns** - Automatic tier transitions
- **Compliance** - Archive then delete per regulations

## Cost Optimization

- **Storage costs** apply to all object versions
- **Delete old versions** when no longer needed
- **Use lifecycle policies** to automate transitions
- **Choose appropriate storage class** based on access patterns