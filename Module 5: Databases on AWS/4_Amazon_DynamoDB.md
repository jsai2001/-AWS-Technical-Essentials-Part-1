# Amazon DynamoDB

## What is DynamoDB?

**DynamoDB:** Fully managed NoSQL database service providing fast, predictable performance with seamless scalability

## Key Characteristics

### NoSQL vs SQL
| Aspect | DynamoDB (NoSQL) | Relational (SQL) |
|--------|------------------|------------------|
| **Schema** | Flexible | Rigid, predefined |
| **Queries** | Simple, single table | Complex, multi-table joins |
| **Scalability** | Highly scalable | Can have scaling issues |
| **Performance** | Millisecond response | Variable under stress |
| **Data variation** | Items can have different attributes | All rows must match schema |

### Core Benefits
- **Fully managed** - No hardware provisioning, setup, patching
- **Auto-scaling** - Handles throughput and storage automatically
- **High availability** - Multi-AZ replication built-in
- **SSD storage** - Fast, durable storage
- **Consistent performance** - Predictable response times

## Core Components

### Tables, Items, and Attributes
- **Table:** Collection of items (like a spreadsheet)
- **Item:** Individual record (like a row)
- **Attribute:** Data field (like a column)
- **Primary Key:** Uniquely identifies each item
- **Secondary Indexes:** Additional query flexibility

### Example Structure
```
Employee Table:
├── Item 1: {employee_id: "001", name: "John", dept: "IT"}
├── Item 2: {employee_id: "002", name: "Jane", dept: "HR", phone: "555-1234"}
└── Item 3: {employee_id: "003", name: "Bob", title: "Manager"}
```

## Use Cases

### When to Choose DynamoDB
- **Scalability problems** with traditional databases
- **Active development** of applications/services
- **OLTP workloads** (Online Transaction Processing)
- **Mission-critical applications** requiring high availability
- **High data durability** requirements

### Application Examples
- **Software applications:** User metadata, caches for millions of users
- **Media metadata:** Real-time video streaming, interactive content
- **Gaming platforms:** Player data, session history, leaderboards
- **Retail experiences:** Shopping carts, inventory tracking, customer profiles

## Employee Directory Implementation

### Simple Migration
1. Navigate to DynamoDB console
2. Create table named "employees"
3. Set "employee_id" as primary key
4. Accept defaults and create
5. Application automatically works with new table

### Why DynamoDB Works Better
- **Simple lookup table** - No complex relationships needed
- **Usage-based pricing** - Pay for actual usage, not running time
- **Variable load** - Handles weekday/weekend usage patterns efficiently

## Security Features

### Data Protection
- **Encryption at rest** - All data encrypted using AWS KMS
- **Multi-AZ storage** - Redundant storage across facilities
- **Network security** - Protected by AWS global security

### Access Control
- **IAM integration** - Control authentication and authorization
- **Temporary credentials** - Use IAM roles for access
- **Least privilege** - Implement minimal required permissions
- **CloudTrail logging** - Track all API activity

### Monitoring
- **CloudTrail events** - Record all DynamoDB activity
- **Key usage tracking** - Monitor encryption key usage
- **Audit trails** - Ongoing record of database events