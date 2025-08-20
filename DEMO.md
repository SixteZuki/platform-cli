# Demo Evidence

This file shows proof that the CLI works as required.

## EC2

### Create
```
python cli.py --profile dev --owner yuval ec2 create --type t3.micro --os amazon-linux
Created i-08e77fa8399edf0a6
```
### List
```
python cli.py --profile dev --owner yuval ec2 list
i-08e77fa8399edf0a6  running  t3.micro
```
### Stop
```
python cli.py --profile dev --owner yuval ec2 stop i-08e77fa8399edf0a6
stopped i-08e77fa8399edf0a6
```
### Start
```
python cli.py --profile dev --owner yuval ec2 start i-08e77fa8399edf0a6
started i-08e77fa8399edf0a6
```
## S3
### Create
```
python cli.py --profile dev --owner yuval s3 create --name yuvalz-bucket-293602529
bucket created: yuvalz-bucket-293602529
```
### Upload
```
python cli.py --profile dev --owner yuval s3 upload --name yuvalz-bucket-293602529 --file test.txt
uploaded test.txt to yuvalz-bucket-293602529
```
### List
```
python cli.py --profile dev --owner yuval s3 list
yuvalz-bucket-293602529
```
## Route53
### Zone list
```
python cli.py --profile dev --owner yuval route53 list
yuvalz-test.com.   Z07829801P6PSA6DVD5J1
```
### Record create
```
python cli.py --profile dev --owner yuval route53 record --zone yuvalz-test.com --action create --type A --name test.yuvalz-test.com --value 1.2.3.4
record CREATE A test.yuvalz-test.com -> 1.2.3.4
```