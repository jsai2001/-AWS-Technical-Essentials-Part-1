# Serverless with AWS Lambda

## What is AWS Lambda?

**AWS Lambda:** Run code without provisioning or managing servers. Supports virtually any application or backend service.

## Key Benefits

- **No server management** - AWS handles infrastructure
- **High availability** - Built-in fault tolerance
- **Automatic scaling** - Scales with demand
- **Subsecond metering** - Pay only for execution time
- **Multiple languages** - Python, Node.js, Java, Go, .NET, Ruby

## Core Concepts

### Function
- Resource containing your code
- Can be created from scratch, blueprint, or container image
- Processes events when invoked

### Trigger
- Defines when function should run
- Integrates with AWS services (S3, API Gateway, DynamoDB, etc.)
- Responds to events automatically

### Event
- JSON document containing data for function to process
- Structure determined by trigger source

### Runtime
- Language-specific environment (Python, Node.js, etc.)
- Can use built-in or custom runtimes

### Handler
- Method that processes events
- Python syntax: `def handler_name(event, context):`

## Deployment Options

### Zip File Archive
- Contains function code and dependencies
- AWS provides OS and runtime

### Container Image
- OCI-compatible container
- Include code, dependencies, OS, and runtime

## Creating a Lambda Function

### Step 1: Function Setup
1. Choose creation method (scratch/blueprint/container)
2. Set function name (e.g., `ResizeImage`)
3. Select runtime (e.g., Python 3.9)
4. Configure IAM role permissions

### Step 2: Add Trigger
1. Select trigger source (S3, API Gateway, etc.)
2. Configure trigger settings (bucket, event type, prefix)
3. Set event filters if needed

### Step 3: Deploy Code
1. Upload zip file or container image
2. Configure handler function
3. Test with sample events

## Common Use Cases

- **Data processing** - Transform and analyze data
- **Real-time streaming** - Process streaming data
- **Web backends** - API endpoints and microservices
- **IoT backends** - Process device data
- **Image processing** - Resize, convert, analyze images
- **Scheduled tasks** - Cron-like functionality

## Billing

- **Requests** - Number of function invocations
- **Duration** - Execution time rounded to nearest 1ms
- **No minimum runtime** - Cost-effective for short executions
- **No idle charges** - Pay only when code runs