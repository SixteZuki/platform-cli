# Platform CLI

This project is a Python CLI tool that manages AWS resources: EC2, S3, and Route53.  
The tool only works on resources that have specific tags so it will not touch other resources in the account.

## What the tool does
- **EC2**: create, list, stop, start instances
- **S3**: create buckets, list buckets, upload files
- **Route53**: create hosted zones and manage DNS records
- **Tagging**: every resource has tags (CreatedBy, Owner, Project, Environment)

## Prerequisites
1. Python 3.9 or higher (tested on Python 3.13.7)
2. AWS CLI installed and configured
3. AWS profile with permissions for EC2, S3 and Route53
4. Git installed

## Installation
Clone the repo and install requirements:
```
git clone https://github.com/SixteZuki/platform-cli.git
cd platform-cli
pip install -r requirements.txt
```

# Usage Examples
## EC2
```
python cli.py --profile dev --owner (your_name) ec2 create --type t3.micro --os amazon-linux
python cli.py --profile dev --owner (your_name) ec2 list
python cli.py --profile dev --owner (your_name) ec2 stop i-0123456789abcdef
python cli.py --profile dev --owner (your_name) ec2 start i-0123456789abcdef
```
## S3
```
python cli.py --profile dev --owner (your_name) s3 create --name test-bucket-$(Get-Random)
python cli.py --profile dev --owner (your_name) s3 upload --name test-bucket-12345 --file test.txt
python cli.py --profile dev --owner (your_name) s3 list
```
## Route53
```
python cli.py --profile dev --owner (your_name) route53 list
python cli.py --profile dev --owner (your_name) route53 record --zone test-test.com --action create --type A --name test.test-test.com --value 1.2.3.4
python cli.py --profile dev --owner (your_name) route53 record --zone test-test.com --action update --type A --name test.test-test.com --value 5.6.7.8
python cli.py --profile dev --owner (your_name) route53 record --zone test-test.com --action delete --type A --name test.test-test.com
```
## Cleanup instructions
To avoid unwanted charges you should clean up the resources created by this CLI.

- **EC2**: stop and start are supported by the CLI. For full termination (delete instance), use the AWS Console or the AWS CLI directly.
- **S3**: bucket creation and upload are supported by the CLI. For full deletion of buckets (must be emptied first), use the AWS Console.
- **Route53**: DNS record creation, update and delete are supported by the CLI. Hosted zone deletion should be done manually from the AWS Console.

## Optional UI
```
pip install streamlit
streamlit run app.py
```