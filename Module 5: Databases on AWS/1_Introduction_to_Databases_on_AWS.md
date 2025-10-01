# Introduction to Databases on AWS

## Database Options on AWS

### Self-Managed on EC2
- **AWS Responsibility:** Physical infrastructure, OS installation
- **Your Responsibility:** Database engine, multi-AZ setup, patching, management
- **Use Case:** Database migration with full control

### Managed Database (RDS)
- **AWS Responsibility:** Infrastructure, patching, upgrades, installation
- **Your Responsibility:** Schema design, indexing, stored procedures, access control
- **Use Case:** Reduce operational overhead

## Relational Databases

### Structure
- **Tables:** Organize data in rows and columns
- **Rows:** Records containing complete entries
- **Columns:** Attributes of entries
- **Relationships:** Links between tables via common attributes
- **Schema:** Fixed structure (difficult to change after deployment)

### Example Structure
```
Books Table: ISBN, Title, Author, Format
Sales Table: Sale_ID, ISBN, Author, Quantity
Authors Table: Author_ID, Author, Biography
```

## Relational Database Management Systems (RDBMS)

### Common Examples
- MySQL
- PostgreSQL
- Oracle
- Microsoft SQL Server
- Amazon Aurora

### Query Language
**SQL (Structured Query Language)**
```sql
SELECT * FROM table_name;
```

## Benefits of Relational Databases

- **Joins:** Query multiple tables to understand relationships
- **Reduced redundancy:** Reference data instead of duplicating
- **Familiarity:** Widely used since 1970s
- **ACID compliance:** Atomicity, Consistency, Isolation, Durability

## Use Cases

### Fixed Schema Applications
- Lift-and-shift migrations
- Applications with stable data structure

### Persistent Storage Applications
- Enterprise Resource Planning (ERP)
- Customer Relationship Management (CRM)
- Commerce and financial applications

## Managed vs Unmanaged Trade-offs

| Aspect | Unmanaged (EC2) | Managed (RDS) |
|--------|-----------------|---------------|
| **Control** | High | Medium |
| **Convenience** | Low | High |
| **Infrastructure** | AWS managed | AWS managed |
| **Database Management** | Customer | AWS managed |
| **Patching/Updates** | Customer | AWS managed |
| **Query Optimization** | Customer | Customer |
| **Data Security** | Customer | Customer |

## Key Decision Factors

**Choose EC2 when:**
- Need full database control
- Custom database configurations
- Specific compliance requirements

**Choose RDS when:**
- Want reduced operational overhead
- Standard database requirements
- Focus on application development