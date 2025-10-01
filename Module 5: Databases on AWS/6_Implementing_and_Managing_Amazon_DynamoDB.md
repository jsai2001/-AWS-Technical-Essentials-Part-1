# Implementing and Managing Amazon DynamoDB

## Overview

Demonstration of creating a DynamoDB table and integrating it with the employee directory application.

## Step 1: Launch Updated EC2 Instance

### Clone Existing Instance
1. Navigate to EC2 → Instances
2. Select `employee-directory-app-s3` instance
3. Actions → Image and templates → "Launch more like this"

### Configure New Instance
1. **Name:** `employee-directory-app-dynamodb`
2. **Key pair:** Use existing key
3. **Auto-assign public IP:** Enable
4. **User data:** Keep S3 bucket configuration
5. Launch instance and wait for 2/2 status checks

### Verify Application
1. Copy public IP address
2. Test application loads in browser
3. Confirm base functionality before proceeding

## Step 2: Create DynamoDB Table

### Table Configuration
1. Navigate to DynamoDB console
2. Click "Create table"
3. **Table name:** `Employees` (matches application expectation)
4. **Partition key:** `id` (String type)
5. Keep all default settings
6. Click "Create table"

### Result
- Table created almost instantly
- Ready for application integration

## Step 3: Test Full Integration

### Add Employee Through Application
1. Access application via public IP
2. Click "Add" to create new employee
3. **Fill form:**
   - Name, location, job title
   - Select badges/preferences
   - Upload employee photo
4. Click "Save"

### Verify Data Storage

#### Check S3 Bucket
1. Navigate to S3 console
2. Open employee photo bucket
3. Confirm uploaded photo appears with generated name

#### Check DynamoDB Table
1. Navigate to DynamoDB console
2. Select "Employees" table
3. Click "Explore table items"
4. **Verify data:**
   - Employee information (name, title, location)
   - Selected badges
   - Photo object name
   - Unique ID (partition key)

## Step 4: Cleanup

1. Keep DynamoDB table running (minimal cost when not in use)
2. Stop EC2 instance to avoid charges
3. S3 bucket retains uploaded photos

## Key Integration Points

### Application Configuration
- **Database name:** Must match "Employees"
- **Partition key:** Must be "id" field
- **Data flow:** App → DynamoDB (metadata) + S3 (photos)

### Verification Process
- **Frontend:** Employee appears in directory
- **S3:** Photo stored with generated filename
- **DynamoDB:** All form data stored as item attributes

## Benefits Demonstrated

- **Seamless integration** between services
- **Automatic scaling** of DynamoDB
- **Cost efficiency** - pay only for usage
- **Data persistence** across application restarts