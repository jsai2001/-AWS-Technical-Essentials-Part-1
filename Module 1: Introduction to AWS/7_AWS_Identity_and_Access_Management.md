# AWS Identity and Access Management (IAM)

## Core Concepts

**Authentication:** Verifies who you are (username/password)  
**Authorization:** Determines what you can do (permissions)

## IAM Components

### IAM Users
- Individual identities for people accessing AWS
- Each person gets unique credentials
- Replace root user for daily operations

### IAM Groups
- Collections of users with similar permissions
- Attach policies to groups, not individual users
- Easier permission management

### IAM Policies
- JSON documents defining permissions
- Specify Effect (Allow/Deny), Action, Resource, Conditions

**Policy Example:**
```json
{
  "Effect": "Allow",
  "Action": "ec2:*",
  "Resource": "*"
}
```

**Example 2:**

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyS3AccessOutsideMyBoundary",
      "Effect": "Deny",
      "Action": [
        "s3:*"
      ],
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:ResourceAccount": [
            "222222222222"
          ]
        }
      }
    }
  ]
}
```

This policy uses a Deny effect to block access to Amazon S3 actions, unless the Amazon S3 resource that's being accessed is in account 222222222222. This ensures that any Amazon S3 principals are accessing only the resources that are inside of a trusted AWS account.

### IAM Roles
- Temporary credentials for applications/services
- No permanent username/password
- Assumed programmatically
- Auto-rotating credentials

## Access Management Scenarios

### AWS Account Access
- **Solution:** IAM Users + Groups + Policies
- **Use for:** Human access to AWS console/CLI

### Service-to-Service Access
- **Solution:** IAM Roles
- **Use for:** EC2 accessing S3, Lambda calling DynamoDB

### Application User Access
- **Solution:** Application-level authentication (not IAM)
- **Use for:** End users logging into your application

## Best Practices

1. **Lock down root user** - Enable MFA, don't use daily
2. **Create admin IAM user** - Use instead of root
3. **Use groups** - Assign policies to groups, not users
4. **Principle of least privilege** - Grant minimum needed permissions
5. **Use roles for services** - Don't create users for applications
6. **Regular cleanup** - Remove unused users/roles/policies

## Setup Workflow

1. Enable MFA on root user
2. Create IAM user with admin permissions
3. Log out of root, log in as IAM user
4. Create additional users, groups, and policies as needed