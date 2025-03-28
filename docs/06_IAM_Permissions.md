# AWS IAM Permissions  

## What are IAM Permissions?  
IAM permissions define what actions an **IAM user, group, or role** can perform on AWS resources. Permissions are assigned using **IAM policies**, which are JSON-based documents specifying allowed or denied actions. IAM permissions can be applied to:  
- **Users** (individual access control)  
- **Groups** (manage permissions for multiple users)  
- **Roles** (grant temporary access to AWS services or external identities)  
- **Other AWS Identities** (such as federated users and services)  

## Types of IAM Permissions  
1. **AWS-Managed Policies** - Predefined policies by AWS (e.g., `AdministratorAccess`, `ReadOnlyAccess`).  
2. **Customer-Managed Policies** - Custom policies created by users for specific requirements.  
3. **Inline Policies** - Directly attached policies to IAM users, groups, or roles (not reusable).  

## Hands-on Lab: Assigning IAM Permissions (AWS Console)  
1. Navigate to **IAM Service** → **Users/Groups/Roles** → Select an entity.  
2. Click **Permissions** → **Attach Policies**.  
3. Search and attach a policy like **AmazonS3FullAccess**.  
4. Click **Save changes**.  

*(Optional: The same actions can be performed via AWS CLI as shown below.)*  

## Hands-on Lab: Assigning IAM Permissions (AWS CLI) *(Optional)*  
### Attach an AWS-Managed Policy to a User  
```sh
aws iam attach-user-policy --user-name developer1 --policy-arn arn:aws:iam::aws:policy/AmazonEC2FullAccess
```

### Attach an AWS-Managed Policy to a Group  
```sh
aws iam attach-group-policy --group-name DevOpsTeam --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess
```

### Attach an AWS-Managed Policy to a Role  
```sh
aws iam attach-role-policy --role-name LambdaExecutionRole --policy-arn arn:aws:iam::aws:policy/AmazonDynamoDBFullAccess
```

### Create and Attach a Custom Policy to a User  
```json
{
   "Version": "2012-10-17",
   "Statement": [
      {
         "Effect": "Allow",
         "Action": [
            "s3:ListBucket",
            "s3:GetObject"
         ],
         "Resource": [
            "arn:aws:s3:::my-bucket",
            "arn:aws:s3:::my-bucket/*"
         ]
      }
   ]
}
```
Attach this policy using:  
```sh
aws iam put-user-policy --user-name developer1 --policy-name S3ReadOnly --policy-document file://s3-policy.json
```

### Check Permissions Assigned to a User  
```sh
aws iam list-attached-user-policies --user-name developer1
```

### Detach a Policy from a User  
```sh
aws iam detach-user-policy --user-name developer1 --policy-arn arn:aws:iam::aws:policy/AmazonEC2FullAccess
```

## Best Practices for IAM Permissions  
- **Follow the Principle of Least Privilege** – Grant only necessary permissions.  
- **Use Groups & Roles Instead of Direct User Permissions** – Easier management.  
- **Enable IAM Access Analyzer** – Detect excessive permissions.  
- **Use Service Control Policies (SCPs) in AWS Organizations** – Restrict permissions at an account level.  
- **Monitor IAM API Calls Using AWS CloudTrail** – Track security events.  


IAM permissions control access to AWS resources and should be carefully managed to maintain security. IAM policies can be assigned to users, groups, and roles to ensure structured access management. Using IAM policies effectively ensures compliance with best practices and security requirements. AWS CLI can be optionally used for automation and scripting purposes.  

