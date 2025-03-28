# AWS IAM Groups  //here i agve readonlyaccesss //see the statement..

## What is an IAM Group?  
An IAM Group is a collection of IAM users that share the same set of permissions. Instead of assigning policies to individual users, you can attach policies to a group, making access management more efficient.  

## Features of IAM Groups  
- **Eases Permissions Management** – Assign policies at the group level instead of individual users.  
- **Users Can Be in Multiple Groups** – A user can belong to multiple groups and inherit permissions from each.  
- **No Direct Credentials** – Groups do not have access keys or passwords, only users do.  
- **Scalable** – Adding or removing users from a group automatically grants or revokes permissions.  

## Common IAM Group Examples  
| Group Name         | Example Policies Attached                   |
|--------------------|-------------------------------------------|
| Admins            | AdministratorAccess                        |
| Developers        | AmazonEC2FullAccess, AWSLambdaFullAccess  |
| Read-Only Users   | ReadOnlyAccess                             |
| Security Team     | IAMReadOnlyAccess, AWSCloudTrailReadOnlyAccess |

## Hands-on Lab: Creating an IAM Group (AWS Console)  
Objective: Create an IAM group and assign permissions.  

### Steps  
1. Login to AWS Console → Go to IAM Service.  
2. Click on "User Groups" → "Create Group."  
3. Enter a Group Name (e.g., `Developers`).  
4. Attach a policy (e.g., `AmazonEC2FullAccess`).  
5. Click "Create Group."  
6. Add users to the group:  
   - Go to "User Groups" → Select `Developers` → Click "Add Users."  
   - Choose users and click "Add to Group."  

Verification: Login as a user in the `Developers` group and check EC2 access.  

## IAM Group Best Practices  
- Use **groups instead of assigning policies directly to users**.  
- Follow the **principle of least privilege** – grant only necessary permissions.  
- Regularly **review and update group permissions** to match business needs.  
- Do not assign **AdministratorAccess** unless absolutely necessary.  
- Use **IAM policies instead of inline policies** for better management.  

## Hands-on Lab: Create an IAM Group via AWS CLI  
Objective was: Created an IAM group and attach policies using AWS CLI.  

### Prerequisites  
- AWS CLI installed  
- IAM credentials configured using `aws configure`  

### Steps  
1. Create an IAM group:  
   ```sh
   aws iam create-group --group-name Developers
2.Attach a policy to the group:
 ```sh
   aws iam attach-group-policy --group-name Developers --policy-arn arn:aws:iam::aws:policy/AmazonEC2FullAccess

3. Add an existing IAM user to the group:
 ```sh
   aws iam add-user-to-group --user-name developer_user --group-name Developers
4. Verify the group and users:
```sh
   aws iam get-group --group-name Developers
 
**Example IAM Policy for a Developer Group**
     {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:*",
                "lambda:*"
            ],
            "Resource": "*"
        }
    ]
}


