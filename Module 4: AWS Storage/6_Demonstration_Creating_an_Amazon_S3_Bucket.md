# Creating an Amazon S3 Bucket

## Overview

Demonstration of creating an S3 bucket and configuring EC2 instance to use it for the employee directory application.

## Step 1: Create S3 Bucket

1. Navigate to S3 console
2. Click "Create bucket"
3. **Bucket name:** `employee-photo-bucket-[initials]-[random-digits]`
   - Example: `employee-photo-bucket-sr-963`
4. **Region:** Same as infrastructure (e.g., us-west-2)
5. Keep all other defaults
6. Click "Create bucket"

## Step 2: Test Object Upload

1. Click on bucket name to enter bucket
2. Click "Upload" → "Add files"
3. Select employee photo file
4. Click "Upload"
5. Verify successful upload

## Step 3: Configure Bucket Policy

### Purpose
Restrict access to application role only (not public access)

### Process
1. Go to bucket → Permissions tab
2. Scroll to "Bucket policy" → Edit
3. Paste bucket policy JSON
4. **Replace placeholders:**
   - `INSERT-ACCOUNT-NUMBER` → Your AWS account number
   - `INSERT-BUCKET-NAME` → Your bucket name (both locations)
   - Remove caret brackets
5. Save changes

### Result
Only the specified IAM role can access bucket and objects

## Step 4: Update EC2 Instance

### Clone Existing Instance
1. Navigate to EC2 → Instances
2. Select stopped instance
3. Actions → Image and templates → "Launch more like this"

### Configure New Instance
1. **Name:** `employee-directory-app-s3`
2. **Image/Instance type:** Keep same
3. **Key pair:** Use existing
4. **Auto-assign public IP:** Enable
5. **Advanced details:**
   - IAM role: Already associated
   - **User data:** Add bucket name to environment variable

### Launch Process
1. Click "Launch instance"
2. Wait for instance to reach "running" state
3. Wait for status checks: 2/2 passed

## Step 5: Verify Application

1. Copy public IP address of new instance
2. Open in browser
3. Confirm application loads (database integration pending)

## Cleanup Tasks

1. Stop the new EC2 instance
2. Delete test object from S3 bucket

## Key Concepts

- **Bucket naming:** Must be globally unique
- **Regional placement:** Keep resources in same region
- **Bucket policies:** Control access at bucket level
- **Instance cloning:** Reuse configurations efficiently
- **Environment variables:** Pass configuration to applications