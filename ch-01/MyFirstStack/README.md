## Creating the Stack:
```bash
aws cloudformation create-stack \
  --stack-name mybucket \
  --template-body file://my_bucket.yaml
```

my_bucket.yaml
```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: This is my first bucket with IaC
Resources:
  MyBucket:
    Type: "AWS::S3::Bucket"
```

<div align="center">
  <img src="/SS/ch-01/MyFirstStack/1.PNG"/>
</div>

#

## Verify bucket:
```bash
aws s3 ls
```

<div align="center">
  <img src="/SS/ch-01/MyFirstStack/2.PNG"/>
</div>

#

## Updating the Stack:
```bash
aws cloudformation update-stack \
  --stack-name mybucket \
  --template-body file://my_bucket_with_public_read.yaml
```

my_bucket_with_public_read
```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: This is my first bucket with IaC
Resources:
  MyBucket:
    Type: "AWS::S3::Bucket"
    Properties:
      AccessControl: PublicRead
```

<div align="center">
  <img src="/SS/ch-01/MyFirstStack/3.PNG"/>
</div>

#

## Verify Update:
```bash
aws cloudformation describe-stacks --stack-name mybucket
```

<div align="center">
  <img src="/SS/ch-01/MyFirstStack/4.PNG"/>
</div>

#

## Verify changes applied:
```bash
aws s3api get-bucket-acl --bucket $YOUR_BUCKET_NAME
```

## Delete the Stack:
```bash
aws cloudformation delete-stack --stack-name mybucket
```

<div align="center">
  <img src="/SS/ch-01/MyFirstStack/my_first_stack.PNG"/>
</div>
