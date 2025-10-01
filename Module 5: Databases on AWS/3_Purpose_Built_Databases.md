# Purpose-Built Databases

## Why Purpose-Built Databases?

**Problem:** Relational databases are like multi-tools - good at many things but not optimized for specific use cases

**Solution:** Choose the right database for each specific workload and data model

## Employee Directory Example

### Original Choice: RDS
- **Issues:** Complex features for simple lookup table, hourly charging regardless of usage
- **Usage pattern:** High weekday usage, no weekend usage

### Better Choice: DynamoDB
- **Benefits:** NoSQL key-value store, millisecond latency, usage-based pricing
- **Fit:** Perfect for simple employee lookup table

## AWS Purpose-Built Database Services

### Amazon DynamoDB
- **Type:** NoSQL (key-value, document)
- **Performance:** Fast, consistent at any scale
- **Billing:** Usage-based (not hourly)
- **Best for:** High-scale applications, serverless applications, OLTP workloads

### Amazon ElastiCache
- **Type:** In-memory caching
- **Engines:** Redis, Memcached
- **Management:** Fully managed (failovers, backups, upgrades)
- **Best for:** Application performance acceleration

### Amazon MemoryDB for Redis
- **Type:** Durable in-memory database
- **Performance:** Microsecond read, single-digit millisecond write latency
- **Durability:** Multi-AZ persistence
- **Best for:** High-performance primary database, microservices

### Amazon DocumentDB
- **Type:** Document database (NoSQL)
- **Compatibility:** MongoDB API compatible
- **Best for:** Content management, user profiles, web/mobile apps

### Amazon Keyspaces
- **Type:** Wide-column NoSQL
- **Compatibility:** Apache Cassandra compatible
- **Best for:** High-volume applications, straightforward access patterns

### Amazon Neptune
- **Type:** Graph database
- **Best for:** Social networks, recommendation engines, fraud detection, knowledge graphs

### Amazon Timestream
- **Type:** Time series database
- **Performance:** 1000x faster than relational databases for time series
- **Best for:** IoT applications, operational monitoring, stock prices

### Amazon QLDB
- **Type:** Ledger database
- **Features:** Immutable, cryptographically verifiable history
- **Best for:** Financial records, supply chain, audit trails, compliance

## Selection Criteria

| Use Case | Recommended Database |
|----------|---------------------|
| Simple lookup tables | DynamoDB |
| Content management | DocumentDB |
| Social networks | Neptune |
| Financial records | QLDB |
| IoT sensor data | Timestream |
| High-scale web apps | Keyspaces |
| Application caching | ElastiCache |
| Real-time applications | MemoryDB |

## Key Benefits

- **Optimized performance** for specific data models
- **Managed services** reduce operational overhead
- **Cost efficiency** through usage-based pricing models
- **Focus on application** rather than database expertise