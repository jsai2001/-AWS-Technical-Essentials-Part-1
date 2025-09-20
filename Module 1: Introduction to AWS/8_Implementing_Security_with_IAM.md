# Implementing Security with IAM

## Creating IAM Roles

### Step 1: Create Role
1. Navigate to IAM → Roles → Create role
2. Select trusted entity type:
   - **AWS service** - For EC2, Lambda, etc.
   - **AWS account** - Cross-account access
   - **Web identity** - Federated users
   - **SAML 2.0** - Corporate directories
3. Choose specific service (e.g., EC2)

### Step 2: Add Permissions
- Select AWS managed policies or create custom policies
- Example policies:
  - `AmazonS3FullAccess` - Full S3 permissions
  - `AmazonDynamoDBFullAccess` - Full DynamoDB permissions
- **Best practice:** Use least privilege (custom policies)

### Step 3: Name and Create
- Provide role name (e.g., `EmployeeWebApp`)
- Review trust policy and permissions
- Create role

## Creating IAM Users

### Step 1: Create User
1. Navigate to IAM → Users → Add users
2. Enter username (e.g., `EC2Admin`)
3. Enable console access (optional)
4. Set password options

### Step 2: Add to Group
1. Create new group or select existing
2. Group name (e.g., `EC2Admins`)
3. Attach policies to group
4. Add user to group

### Step 3: Review Permissions
- User inherits group permissions
- Additional direct permissions (e.g., `IAMUserChangePassword`)

## Access Keys

### Purpose
- Enable programmatic access to AWS APIs
- Used with AWS CLI and SDKs
- Alternative to console access

### Creation Process
1. Go to user → Security credentials → Access keys
2. Select use case (e.g., Command Line Interface)
3. Acknowledge recommendations
4. Create access key pair:
   - **Access Key ID** - Public identifier
   - **Secret Access Key** - Private key (keep secure)

### Security Best Practices
- Deactivate unused access keys
- Delete unnecessary access keys
- Use IAM roles instead when possible
- Consider AWS CloudShell as alternative

## Key Concepts

**Trust Policy:** Defines who can assume the role  
**Permissions Policy:** Defines what actions are allowed  
**Managed Policies:** AWS-created and maintained  
**Custom Policies:** User-created for specific needs  
**Access Keys:** Credentials for programmatic access