# Protecting the AWS Root User

## What is the AWS Root User?

The root user is created when you first create an AWS account using an email and password. It has **complete access** to all AWS services and resources.

## Root User Credentials

**Console Access:**
- Email address and password used to create the account

**Programmatic Access:**
- Access Key ID (e.g., A2lAl5EXAMPLE)
- Secret Access Key (e.g., wJalrFE/KbEKxE)

## Root User Best Practices

1. **Enable MFA immediately** after account creation
2. **Use strong password**
3. **Delete access keys** (create only if absolutely necessary)
4. **Never share credentials**
5. **Don't use for everyday tasks** - create IAM users instead

## Multi-Factor Authentication (MFA)

MFA requires **two or more** authentication methods:

### Authentication Categories
- **Something you know** - Password, PIN
- **Something you have** - Phone app, hardware token
- **Something you are** - Fingerprint, face scan

### Supported MFA Devices

| Type | Examples | Security Level |
|------|----------|----------------|
| **Virtual MFA** | Google Authenticator, Microsoft Authenticator, Authy | Good |
| **Hardware TOTP** | Key fob, display card | Better |
| **FIDO Security Keys** | YubiKey, hardware security keys | Best |

## Why MFA Matters

Without MFA: Email + Password = Account Access  
With MFA: Email + Password + MFA Code = Account Access

Even if password is compromised, account remains secure.

## Key Takeaway

**Root user = Maximum power = Maximum protection needed**

Enable MFA immediately and use IAM users for daily operations.