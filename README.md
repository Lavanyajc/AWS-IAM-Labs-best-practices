##hii there!,,this is lavanya jc ,I have practised this and putting everthing here in well structured format.
# AWS IAM Labs  

## Introduction  
This repository contains hands-on labs for **AWS Identity and Access Management (IAM)**, covering **Users, Groups, Roles, Policies, Permissions, and more**. These labs provide step-by-step guides for both **AWS Console** and **AWS CLI (optional)**, making it easier to understand and implement IAM concepts in real-world scenarios.  

## Prerequisites  
Before using this repository, ensure you have:  
- An **AWS account** with necessary permissions.  
- If using **AWS CLI (optional)**:  
  - Installed AWS CLI (see instructions below).  
  - Configured AWS credentials using `aws configure`.  

## File Structure & Usage  
Each file in the **`docs/`** directory contains detailed explanations and hands-on labs for different IAM components.  

| File Name                  | Description | AWS CLI Optional? |
|----------------------------|-------------|-------------------|
| `IAM_Overview.md`          | Basic concepts of IAM | ❌ (Only Console) |
| `IAM_Users.md`             | Creating and managing IAM users | ✅ (CLI Commands Available) |
| `IAM_Groups.md`            | Creating and managing IAM groups | ✅ (CLI Commands Available) |
| `IAM_Roles.md`             | IAM roles and cross-account access | ✅ (CLI Commands Available) |
| `IAM_Permissions.md`       | How to assign permissions to users, groups, and roles | ✅ (CLI Commands Available) |
| `IAM_Policies.md`          | AWS-managed and custom IAM policies | ✅ (CLI Commands Available) |
| `IAM_AccessKeys.md`        | Managing IAM access keys securely | ✅ (CLI Commands Available) |
| `IAM_CloudFront.md`        | Optional IAM integration with AWS CloudFront | ✅ (CLI Commands Available) |
| `IAM_Fundamentals.md`      | Core IAM principles and best practices | ❌ (Only Console) |

## Using AWS CLI (Optional)  
For automation, AWS CLI can be used instead of the AWS Console. The commands for AWS CLI are included in each relevant file where applicable.  

### Install AWS CLI  
#### Windows:  
```sh
curl "https://awscli.amazonaws.com/AWSCLIV2.msi" -o "AWSCLIV2.msi"
msiexec.exe /i AWSCLIV2.msi /quiet
```

```
#### Verify Installation:  
```sh
aws --version
```
#### Configure AWS CLI:  
```sh
aws configure
```
You will be prompted to enter:  
- AWS **Access Key ID**  
- AWS **Secret Access Key**  
- **Region** (e.g., `us-east-1`)  
- **Output format** (default: `json`)
  ## you will get these access keys by following the file of access keys 

## How to Navigate  
- If you are new to IAM, start with **`IAM_Overview.md`**.  
- To create users, groups, or roles, refer to **`IAM_Users.md`**, **`IAM_Groups.md`**, and **`IAM_Roles.md`**.  
- To understand permissions, see **`IAM_Permissions.md`** and **`IAM_Policies.md`**.  
- If you're working with programmatic access, refer to **`IAM_AccessKeys.md`**.  
- For optional IAM integration with **CloudFront**, see **`IAM_CloudFront.md`**.  

## Contributing  
If you want to contribute to this repository, feel free to create a **pull request** or raise an **issue**.  

  
This repository serves as a complete guide to mastering **AWS IAM** with hands-on labs. Follow the files in sequence for structured learning. Use the **AWS Console** for a graphical approach and **AWS CLI (optional)** for automation. 🚀  
