# Devops
Basic steps:
1. launch instance
2. create key-value pair and save the .pem file.
3. use the public IP.
4. to login to the ec2 instance: "ssh -i location/to/the/.pem file ubuntu@public IP " (we are using ubuntu because we have crrated ubuntu machine(ec2)).

# Ways to create an EC2 Instaance:
1. AWS CLI: we have to download AWS CLI in our computer and do aws configure.

note: for reference visit: https://docs.aws.amazon.com/efs/latest/ug/gs-step-one-create-ec2-resources.html
# List Bucket:
> aws s3 ls
# Create Bucket:
> aws s3 mb s3://bucket_name

2. By CFT(CLoud Formation Template): simply we need to copy the script and the service will be created.
Refer: https://github.com/awslabs/aws-cloudformation-templates .

Note: for automation of this processes we can use programming languages like python , python uses Boto3 library.
 Link to the documentation: https://boto3.amazonaws.com/v1/documentation/api/latest/index.html

 # To list all the s3 buckets using boto3:
   
   import boto3
   s3 = s3.resource('s3')
   for bucket in s3.buckets.all():
       print(bucket.name)

 !! we can find the scripts for listing ec2 and other services as well, in the boto3 documentation.
 



