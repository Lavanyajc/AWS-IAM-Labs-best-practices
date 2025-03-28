# AWS IAM CloudFront Access (Optional for CLI) ##mostly not used much compare to cli. but needed not mandatorly required //best for uploading and downloading files...used mainly for get commands 

## What is AWS CloudFront?  
Amazon CloudFront is a content delivery network (CDN) that delivers data, videos, applications, and APIs securely with low latency. It integrates with AWS services like S3, EC2, and Lambda@Edge.  

## CloudFront & IAM Integration  
- IAM users can be granted permissions to manage CloudFront distributions.  
- Access can be restricted using **IAM Policies** and **OAC (Origin Access Control)**.  

## Hands-on Lab: Granting IAM User Access to CloudFront (AWS Console)  
1. Go to **IAM Service** → **Users** → Select a user.  
2. Click **Add permissions** → **Attach policies directly**.  
3. Search for **CloudFrontFullAccess** or create a custom policy.  
4. Attach the policy and click **Save changes**.  

## Hands-on Lab: Granting IAM User Access to CloudFront (AWS CLI)  
### Attach CloudFrontFullAccess Policy to a User  
```sh
aws iam attach-user-policy --user-name developer1 --policy-arn arn:aws:iam::aws:policy/CloudFrontFullAccess
```

### Create a Custom IAM Policy for Limited CloudFront Access  
```json
{
   "Version": "2012-10-17",
   "Statement": [
      {
         "Effect": "Allow",
         "Action": [
            "cloudfront:ListDistributions",
            "cloudfront:GetDistribution",
            "cloudfront:GetDistributionConfig"
         ],
         "Resource": "*"
      }
   ]
}
```
Attach this policy using:  
```sh
aws iam put-user-policy --user-name developer1 --policy-name CloudFrontReadOnly --policy-document file://cloudfront-policy.json
```

## Hands-on Lab: Managing CloudFront Distributions (AWS CLI)  
### List All CloudFront Distributions  
```sh
aws cloudfront list-distributions
```

### Get Details of a Specific Distribution  
```sh
aws cloudfront get-distribution --id E123EXAMPLE
```

### Create a New CloudFront Distribution  
```sh
aws cloudfront create-distribution --origin-domain-name example.com
```

## Best Practices for IAM and CloudFront  
- **Use IAM roles** instead of user-based access for CloudFront management.  
- **Restrict permissions** to the required actions only.  
- **Enable OAC (Origin Access Control)** to secure S3-origin content.  
- **Monitor CloudFront API usage** using AWS CloudTrail.  

 
IAM permissions for CloudFront should be granted carefully to avoid excessive access. Using IAM roles and CloudFront security features like OAC ensures better security and management.  
