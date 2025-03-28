
# AWS IAM Users  

## What is an IAM User?  
An IAM User is an entity in AWS that represents a person or application that interacts with AWS services using credentials such as a username, password, or access keys.  

## Key Features of IAM Users  
- **Individual Access** – IAM Users are unique for each person/application.  
- **Customizable Permissions** – Users get access through IAM Policies.  
- **Supports MFA** – Multi-Factor Authentication enhances security.  
- **Access Keys for Programmatic Access** – Users can interact with AWS CLI & SDKs.  

## IAM Users vs. IAM Roles  
| Feature | IAM User | IAM Role |
|---------|---------|---------|
| **Purpose** | For individuals or applications needing permanent credentials | For temporary access by AWS services, users, or external accounts |
| **Authentication** | Username & password or access keys | Assumed using `sts:AssumeRole` |
| **Best Use Case** | Long-term access with fine-grained permissions | Temporary access for AWS services or cross-account users |

## Hands-on Lab: Creating an IAM User (AWS Console)  
1. Navigate to **IAM Service** → **Users** → **Create User**.  
2. Provide a username (e.g., `developer1`).  
3. Select **AWS Management Console access** (for UI access) or **Programmatic access** (for CLI/SDK access).  
4. Attach a policy (e.g., `AdministratorAccess` or `AmazonS3FullAccess`).  
5. Review and create the user.  
6. Download the credentials (`.csv` file) for future use.  

## Hands-on Lab: Creating an IAM User via AWS CLI  
1. Create an IAM user:  
   ```sh
   aws iam create-user --user-name developer1
   ```
2. Attach a policy to grant access:  
   ```sh
   aws iam attach-user-policy --user-name developer1 --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess
   ```
3. Create an access key for CLI/SDK access:  
   ```sh
   aws iam create-access-key --user-name developer1
   ```
4. Verify user details:  
   ```sh
   aws iam get-user --user-name developer1
   ```

## IAM User Permissions  
IAM Users gain permissions via **IAM Policies**, which define what actions they can perform on AWS resources.  

### Example IAM Policy for S3 Read-Only Access  
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::my-bucket",
                "arn:aws:s3:::my-bucket/*"
            ]
        }
    ]
}
```

## Best Practices for IAM Users  
- **Follow Least Privilege** – Grant only necessary permissions.  
- **Enable MFA** – Add extra security for login access.  
- **Use IAM Groups** – Manage permissions efficiently by grouping users.  
- **Rotate Credentials** – Periodically change access keys for security.  
- **Monitor User Activity** – Use **AWS CloudTrail** for auditing.  


IAM Users provide controlled, secure access to AWS resources. Best practices like least privilege, MFA, and credential rotation enhance security and governance.  




