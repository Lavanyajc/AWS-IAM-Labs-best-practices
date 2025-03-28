# AWS IAM Access Keys  

## What are IAM Access Keys?  
IAM Access Keys are credential pairs used for programmatic access to AWS services via the AWS CLI, SDKs, and APIs. Each key consists of:  
- **Access Key ID** – A public identifier.  
- **Secret Access Key** – A private key used for authentication.  

## Key Features of IAM Access Keys  
- **Used for CLI, SDK, and API access** – Not for AWS Management Console login.  
- **Each IAM user can have up to two access keys** – Helps with rotation.  
- **Secret Access Key is shown only once** – Must be stored securely.  
- **Can be deactivated or deleted** – For security management.  

## Hands-on Lab: Creating IAM Access Keys (AWS Console)  
1. Navigate to **IAM Service** → **Users** → Select a user.  
2. Go to the **Security credentials** tab.  
3. Click **Create Access Key**.  
4. Copy the **Access Key ID** and **Secret Access Key**.  
5. Download the `.csv` file for backup.  

## Hands-on Lab: Creating IAM Access Keys via AWS CLI  
1. Create an access key for an IAM user:  
   ```sh
   aws iam create-access-key --user-name developer1
   ```
2. Output Example:  
   ```json
   {
       "AccessKey": {
           "UserName": "developer1",
           "AccessKeyId": "AKIAEXAMPLE123456",
           "Status": "Active",
           "SecretAccessKey": "abcd1234example5678",
           "CreateDate": "2024-03-28T12:00:00Z"
       }
   }
   ```
3. Configure the AWS CLI with the new access key:  ## here we must need cli to get access
   ```sh
   aws configure
   ```
   - Enter the **Access Key ID** and **Secret Access Key** when prompted.  

## Managing IAM Access Keys  
### Deactivating an Access Key  
To temporarily disable an access key:  
```sh
aws iam update-access-key --user-name developer1 --access-key-id AKIAEXAMPLE123456 --status Inactive
```

### Deleting an Access Key  
To permanently delete an access key:  
```sh
aws iam delete-access-key --user-name developer1 --access-key-id AKIAEXAMPLE123456
```

### Listing Active Access Keys for a User  
```sh
aws iam list-access-keys --user-name developer1
```

## Best Practices for IAM Access Keys  
- **Use IAM Roles instead of Access Keys** whenever possible.  
- **Enable MFA** for users with access keys.  
- **Rotate access keys regularly** to prevent unauthorized access.  
- **Store keys securely** in AWS Secrets Manager or environment variables.  
- **Monitor access key usage** with AWS CloudTrail logs.  
 
IAM Access Keys provide programmatic access to AWS services but should be managed carefully with security best practices. Using IAM roles instead of access keys enhances security and reduces the risk of credential leaks.  

