"# AW# AWS IAM Labs  

# Introduction  
This repository contains hands-on labs for **AWS Identity and Access Management (IAM)**, covering **Users, Groups, Roles, Policies, Permissions, and more**. These labs provide step-by-step guides for both **AWS Console** and **AWS CLI (optional)**, making it easier to understand and implement IAM concepts in real-world scenarios.  

## How to Use This Repository  
Each file in the **`docs/`** directory contains detailed explanations and hands-on labs for different IAM components. If you're using the **AWS Console**, follow the instructions under the console section. If you prefer automation, you can use the **AWS CLI**, which is marked as optional wherever applicable.  

### Files and Their Purpose  
| File Name                  | Description | AWS CLI Optional? |
|----------------------------|-------------|-------------------|
| `IAM_Overview.md`          | Basic concepts of IAM | ❌ No |
| `IAM_Users.md`             | Creating and managing IAM users | ✅ Yes |
| `IAM_Groups.md`            | Creating and managing IAM groups | ✅ Yes |
| `IAM_Roles.md`             | IAM roles and cross-account access | ✅ Yes |
| `IAM_Permissions.md`       | How to assign permissions to users, groups, and roles | ✅ Yes |
| `IAM_Policies.md`          | AWS-managed and custom IAM policies | ✅ Yes |
| `IAM_AccessKeys.md`        | Managing IAM access keys securely | ✅ Yes |
| `IAM_CloudFront.md`        | Optional IAM integration with AWS CloudFront | ✅ Yes |
| `IAM_Fundamentals.md`      | Core IAM principles and best practices | ❌ No |

## How to Navigate and Refer to Files  
- If you are new to IAM, start with **`IAM_Overview.md`**.  
- To create users, groups, or roles, refer to **`IAM_Users.md`**, **`IAM_Groups.md`**, and **`IAM_Roles.md`**.  
- To understand permissions, see **`IAM_Permissions.md`** and **`IAM_Policies.md`**.  
- If you're working with programmatic access, refer to **`IAM_AccessKeys.md`**.  
- For optional IAM integration with **CloudFront**, see **`IAM_CloudFront.md`**.  

## Using AWS CLI (Optional)  
For automation, AWS CLI can be used instead of the AWS Console. The commands for AWS CLI are included in each relevant file where applicable. You can install AWS CLI and configure it using the following commands:  

```sh
# Install AWS CLI (if not installed)
curl "https://awscli.amazonaws.com/AWSCLIV2.msi" -o "AWSCLIV2.msi"
msiexec.exe /i AWSCLIV2.msi /quiet

# Configure AWS CLI with your credentials
aws configure
```

## Contributing  
If you want to contribute to this repository, feel free to create a pull request or raise an issue.  

 
This repository serves as a complete guide to mastering **AWS IAM** with hands-on labs. Follow the files in sequence for structured learning. Use the **AWS Console** for a graphical approach and **AWS CLI (optional)** for automation.  

 
