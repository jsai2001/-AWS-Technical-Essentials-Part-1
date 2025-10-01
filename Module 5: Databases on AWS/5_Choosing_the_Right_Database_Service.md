# Choosing the Right Database Service

## AWS Database Portfolio

| Database Type | AWS Services | Use Cases |
|---------------|--------------|-----------|
| **Relational** | RDS, Aurora, Redshift | Traditional apps, ERP, CRM, ecommerce |
| **Key-Value** | DynamoDB | High-traffic web apps, ecommerce, gaming |
| **In-Memory** | ElastiCache (Redis/Memcached) | Caching, session management, leaderboards |
| **Document** | DocumentDB | Content management, catalogs, user profiles |
| **Wide Column** | Keyspaces (Cassandra) | Industrial apps, fleet management, IoT |
| **Graph** | Neptune | Fraud detection, social networks, recommendations |
| **Time Series** | Timestream | IoT applications, DevOps, industrial telemetry |
| **Ledger** | QLDB | Supply chain, banking, systems of record |

## Modern Database Strategy

### Traditional Approach
- **One database** supports entire application
- **One-size-fits-all** mentality
- **Limitations** in performance and scale

### Modern Approach
- **Multiple databases** per application
- **Purpose-built** for specific services
- **Complementary strategy** using best tool for each job

### Benefits
- **Optimized performance** for each workload
- **Better scalability** through specialized databases
- **Cost optimization** by matching service to need
- **Reduced complexity** in individual database operations

## Selection Criteria

**Choose based on:**
- **Data model** requirements
- **Performance** needs
- **Scale** requirements
- **Cost** considerations
- **Operational** complexity tolerance