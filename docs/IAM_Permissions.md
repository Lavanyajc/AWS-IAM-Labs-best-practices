# AWS Identity and Access Management (IAM)

## 1. Introduction to IAM
- **AWS IAM** is a service that helps control **who can access AWS resources** and **what actions** they can perform.
- It provides **secure access control** through **users, groups, roles, and policies**.
- **Free service** included with AWS.

## 2. Key IAM Components  
| **Component**  | **Purpose** |
|--------------|------------|
| **Users**   | Individual AWS accounts with specific permissions. |
| **Groups**  | Collection of users that share common permissions. |
| **Roles**   | Temporary permissions assigned to AWS services or users. |
| **Policies** | JSON-based documents defining permissions for users, groups, and roles. |

## 3. IAM Best Practices  
✅ **Follow the Principle of Least Privilege** – Grant only necessary permissions.  
✅ **Enable Multi-Factor Authentication (MFA)** – Adds an extra layer of security.  
✅ **Use IAM Roles for EC2 & AWS Services** – Avoid storing credentials in applications.  
✅ **Rotate Access Keys Regularly** – Reduces the risk of compromised credentials.  
✅ **Monitor IAM Activity** – Use AWS CloudTrail to track changes and access logs.  

## 4. IAM Policies  
- IAM policies define **permissions using JSON format**.  
- Example of a basic IAM policy granting read-only access to S3:  

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::example-bucket"
    }
  ]
}
