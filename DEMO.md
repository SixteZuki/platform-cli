# 📂 Demo Evidence

This file shows **proof that the Platform CLI works as expected**.  
All commands were executed using the AWS profile **dev** with owner **yuval**.

---

## 💻 EC2

### ✅ Create
```
python cli.py --profile dev --owner yuval ec2 create --type t3.micro --os amazon-linux
Created i-08e77fa8399edf0a6
```
### 📋 List
```
python cli.py --profile dev --owner yuval ec2 list
i-08e77fa8399edf0a6  running  t3.micro
```
### ⏸ Stop
```
python cli.py --profile dev --owner yuval ec2 stop i-08e77fa8399edf0a6
stopped i-08e77fa8399edf0a6
```
### ▶️ Start
```
python cli.py --profile dev --owner yuval ec2 start i-08e77fa8399edf0a6
started i-08e77fa8399edf0a6
```
### 🗑 Terminate
```
python cli.py --profile dev --owner yuval ec2 terminate i-08e77fa8399edf0a6
Terminated i-08e77fa8399edf0a6
```
## 📦 S3
### ✅ Create
```
python cli.py --profile dev --owner yuval s3 create --name yuvalz-bucket
bucket created: yuvalz-bucket-293602529
```
### 📤 Upload
```
python cli.py --profile dev --owner yuval s3 upload --name yuvalz-bucket-293602529 --file test.txt
uploaded test.txt to yuvalz-bucket-293602529
```
### 📋 List
```
python cli.py --profile dev --owner yuval s3 list
yuvalz-bucket-293602529
```
## 🌍 Route53
### ✅ Create
```
python cli.py --profile dev --owner yuval route53 create-zone --name yuval-test.com
yuval-test.com Z019789317KPBDXPYXJA1
```
### 📋 Zone list
```
python cli.py --profile dev --owner yuval route53 list
yuval-test.com. Z019789317KPBDXPYXJA1
```
### 📝 Record create
```
python cli.py --profile dev --owner yuval route53 record --zone yuvalz-test.com --action create --type A --name test.yuvalz-test.com --value 1.2.3.4
record CREATE A test.yuval-test.com -> 1.2.3.4
```
### 🔄 Record update
```
python cli.py --profile dev --owner yuval route53 record --zone yuval-test.com --action update --type A --name test.yuval-test.com --value 5.6.7.8
record UPSERT A test.yuval-test.com -> 5.6.7.8
```