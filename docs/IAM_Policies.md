# AWS IAM Policies // as we can see only start and stop has full access to resources right...u can change it accordingly. 

## What is an IAM Policy?  
An IAM Policy is a JSON document that defines permissions for AWS resources. Policies can be attached to IAM users, groups, or roles to control access.  

## Types of IAM Policies  
1. **AWS-Managed Policies** – Predefined policies by AWS (e.g., `AdministratorAccess`, `AmazonS3ReadOnlyAccess`).  
2. **Customer-Managed Policies** – Custom policies created and managed by users.  
3. **Inline Policies** – Policies embedded directly within a user, group, or role.  

## IAM Policy Structure  
An IAM policy consists of the following elements:  
  { "Version": "2012-10-17", "Statement": [ { "Effect": "Allow", "Action": "s3:ListBucket", "Resource": "arn:aws:s3:::example-bucket" } ] }

### Key Components  
- **Version** – Defines policy language version.  
- **Statement** – Contains multiple permission rules.  
- **Effect** – Defines whether to allow or deny actions.  
- **Action** – Specifies allowed or denied AWS operations.  
- **Resource** – Specifies AWS resources the policy applies to.  

## Hands-on Lab: Creating a Custom IAM Policy (AWS Console)  
### Steps  
1. Navigate to **IAM Service** → **Policies** → **Create Policy**.  
2. Click **JSON** and enter the following:  
     { "Version": "2012-10-17", "Statement": [ { "Effect": "Allow", "Action": ["ec2:StartInstances", "ec2:StopInstances"], "Resource": "*" } ] }


3. Click **Next**, name the policy `EC2StartStopPolicy`, and create it.  
4. Attach this policy to a user or group.  

## Hands-on Lab: Attaching a Policy via AWS CLI  
1. Create a policy and attach it:  
        aws iam create-policy --policy-name EC2StartStopPolicy --policy-document file://ec2_policy.json aws iam attach-group-policy --group-name Developers --policy-arn arn:aws:iam::aws:policy/EC2StartStopPolicy aws iam list-attached-group-policies --group-name Developers



## Example IAM Policies  
| Policy Name | Description |
|-------------|-------------|
| ReadOnlyAccess | Grants read-only access to AWS resources. |
| PowerUserAccess | Grants all permissions except IAM management. |
| S3FullAccess | Provides full access to Amazon S3. |

# Best Practices for IAM Policies  
- Use **least privilege** – grant only necessary permissions.  
- Prefer **AWS-Managed Policies** where possible.  
- Use **customer-managed policies** for custom security needs.  
- Avoid **wildcards (`*`) in resource definitions**, unless necessary.  
- Regularly review and audit IAM policies.  


IAM Policies define access permissions in AWS. By structuring policies correctly and following best practices, you can enforce strong security while enabling necessary operations. Hands-on labs provide practical experience in managing IAM policies effectively.  
   

   
