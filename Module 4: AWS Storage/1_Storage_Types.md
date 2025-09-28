# Storage Types

## Three Categories of Storage

1. **File Storage** - Data stored as files in hierarchical folders
2. **Block Storage** - Data stored in fixed-size blocks with addresses
3. **Object Storage** - Data stored as objects in flat buckets

## File Storage

### Structure
- Hierarchical tree structure with folders/subfolders
- Each file has metadata (name, size, creation date, path)
- Example path: `computer/Application_files/Cat_photos/cats-03.png`

### Use Cases
- **Web serving** - Familiar protocols and permissions
- **Analytics** - File locking and partial file writes
- **Media/Entertainment** - NFS/SMB protocols for content production
- **Home directories** - Scalable user file access

### Best For
- Centralized access across multiple hosts
- Shared file management
- Applications requiring file system protocols

## Block Storage

### Structure
- Files split into fixed-size blocks with unique addresses
- No metadata except addresses
- Direct access to individual blocks

### Advantages
- **Fast access** - Direct route to data
- **Efficient updates** - Change only affected blocks
- **Low latency** - Optimized for performance

### Use Cases
- **Transactional workloads** - Mission-critical databases
- **Containers** - Portable application storage
- **Virtual machines** - VM file systems and boot volumes

### Best For
- High-performance enterprise workloads
- I/O-intensive applications
- Low-latency requirements

## Object Storage

### Structure
- Objects stored in flat buckets (no hierarchy)
- Each object has unique identifier + metadata
- Entire object must be updated for any changes

### Characteristics
- **Scalable** - No limit on number of objects
- **Durable** - Built-in replication
- **Cost-effective** - Pay for what you uses

### Use Cases
- **Data archiving** - Long-term retention, regulatory compliance
- **Backup/Recovery** - Cross-region replication
- **Rich media** - Videos, images, music distribution

### Best For
- Large or unstructured datasets
- Static content (rarely modified)
- Web applications serving media

## Storage Comparison

| Aspect | File | Block | Object |
|--------|------|-------|--------|
| **Structure** | Hierarchical | Addressed blocks | Flat buckets |
| **Access** | File path | Block address | Unique identifier |
| **Updates** | File-level | Block-level | Object-level |
| **Performance** | Medium | High | Medium |
| **Scalability** | Limited | High | Unlimited |

## Traditional Equivalents

- **Block Storage** ≈ Direct-Attached Storage (DAS) / Storage Area Network (SAN)
- **File Storage** ≈ Network-Attached Storage (NAS)
- **Object Storage** ≈ Cloud-native (no direct traditional equivalent)

## Application Example

**Employee Directory Application:**
- **Static photos** → Object storage (accessed often, modified rarely)
- **Application/system files** → Block storage (high transaction rates, frequent updates)