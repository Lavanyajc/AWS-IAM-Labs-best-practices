# AWS IAM Users  

## What is an IAM User?  
An IAM User is an entity that represents an individual or service that interacts with AWS resources. Each user has unique credentials (password and/or access keys) and specific permissions.  

## Features of IAM Users  
- Unique Credentials – Each user has a username, password, and optional access keys.  
- Fine-Grained Permissions – Users can be granted permissions via policies.  
- Multi-Factor Authentication (MFA) – Enhances security for user logins.  
- No Default Permissions – Users have no access until explicitly granted.  
- Can Be Assigned to Groups – Users inherit permissions from groups.  

## Types of IAM User Authentication  
1. Password Authentication – Used for AWS Management Console access.  
2. Access Key Authentication – Used for AWS CLI, SDKs, and API access.  

## Hands-on Lab: Creating an IAM User (AWS Console)  
Objective: Create an IAM user and assign basic permissions.  

### Steps  
1. Login to AWS Console → Go to IAM Service.  
2. Click on Users → Add users.  
3. Enter a username ( developer_user).  
4. Select AWS Management Console Access or Programmatic Access.  
5. Assign the user to an IAM Group (Optional but recommended).  
6. Attach IAM Policies ( AmazonS3ReadOnlyAccess).  
7. Click Next → Review → Create user.  
8. Download the Access Key & Secret Key (if programmatic access is enabled).  

Verification: Log out and sign in with the new user credentials.  

## IAM User Best Practices  
- Use Groups for Access Control – Assign users to groups instead of managing permissions individually.  
- Enable MFA for IAM Users – Adds an extra security layer.  
- Do Not Share IAM Credentials – Each user should have a unique account.  
- Rotate Access Keys Regularly – Reduce security risks.  
- Follow Least Privilege Principle – Grant only necessary permissions.  

## Hands-on Lab: Create an IAM User via AWS CLI  
Objective: Create an IAM user using AWS CLI.  

### Prerequisites  
- AWS CLI installed  
- IAM credentials configured using `aws configure`  

### Steps  
1. Run the following command to create a user:  
   ```sh
   aws iam create-user --user-name developer_user

CLI Commands used ::

'''aws iam attach-user-policy --user-name developer_user --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess'''

''aws iam create-access-key --user-name developer_user''
''aws iam list-users''

""Example IAM Policy for Read-Only S3 Access""

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




