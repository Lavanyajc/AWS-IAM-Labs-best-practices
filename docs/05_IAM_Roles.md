# AWS IAM Roles  //IAM Roles can be created using either the **AWS Management Console** or the **AWS CLI**. not only this any users or groups even. 

## What is an IAM Role?  
An IAM Role is an AWS identity that allows temporary access to resources without needing long-term credentials. It is assumed by trusted entities like AWS services, users, or applications.  

## Key Features of IAM Roles  
- **Temporary Security Credentials** – Roles provide short-lived credentials via AWS STS (Security Token Service).  
- **No Passwords or Access Keys** – Unlike IAM users, roles do not have static credentials.  
- **Cross-Account Access** – Roles can grant access to AWS accounts, third-party services, or federated users.  
- **Service Roles** – Many AWS services (e.g., EC2, Lambda) use IAM roles to interact with other AWS resources.  

## IAM Role Trust Policy Structure  
IAM roles require a **trust policy**, which defines who can assume the role.  

### Example Trust Policy  
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "ec2.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```
### Key Components  
- **Effect** – `Allow` or `Deny`.  
- **Principal** – Defines the entity (user, AWS service) allowed to assume the role.  
- **Action** – `sts:AssumeRole` enables role assumption.  

## Hands-on Lab: Creating an IAM Role for EC2  
### Steps (AWS Console)  
1. Navigate to **IAM Service** → **Roles** → **Create Role**.  
2. Select **AWS Service** → **EC2**.  
3. Attach an existing policy (e.g., `AmazonS3FullAccess`).  
4. Name the role `EC2S3AccessRole` and create it.  
5. Attach the role to an EC2 instance:  
   - Open EC2 → Select instance → Actions → Security → Modify IAM Role → Attach `EC2S3AccessRole`.  

## Hands-on Lab: Creating an IAM Role via AWS CLI  
1. Create a JSON file (`trust-policy.json`) with the following content:  
   ```json
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Effect": "Allow",
               "Principal": {
                   "Service": "ec2.amazonaws.com"
               },
               "Action": "sts:AssumeRole"
           }
       ]
   }
   ```
2. Create the IAM role:  
   ```sh
   aws iam create-role --role-name EC2S3AccessRole --assume-role-policy-document file://trust-policy.json
   ```
3. Attach the S3 access policy:  
   ```sh
   aws iam attach-role-policy --role-name EC2S3AccessRole --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess
   ```
4. Verify the role:  
   ```sh
   aws iam list-attached-role-policies --role-name EC2S3AccessRole
   ```

## Use Cases of IAM Roles  
| Use Case | Description |
|----------|------------|
| **EC2 Roles** | Allows EC2 instances to access S3, DynamoDB, etc. |
| **Lambda Roles** | Enables Lambda functions to interact with AWS services. |
| **Cross-Account Access** | Grants permissions to users from another AWS account. |
| **Federated Access** | Provides temporary access for users from an external identity provider (e.g., Google, Active Directory). |

## Best Practices for IAM Roles  
- Follow **least privilege** – Assign only necessary permissions.  
- Use **separate roles for different applications**.  
- Regularly **review role permissions** to ensure security.  
- Enable **MFA (Multi-Factor Authentication)** for critical roles.  
- Rotate credentials for **temporary access security**.  

 
IAM Roles provide secure, temporary access to AWS services without the need for static credentials. Proper implementation and best practices ensure security and controlled access across AWS environments.  
