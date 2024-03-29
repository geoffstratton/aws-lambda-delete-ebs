Repo Name
=========
aws-lambda-delete-ebs

Description
---------------
AWS Lambda function for deleting unattached EBS volumes, using Python (tested with 3.7), Amazon's boto3 SDK, and some method of invoking the Lambda functions at specified times (e.g., a CloudWatch cron job).

Prerequisites
---------------
* The [boto3 SDK](https://aws.amazon.com/sdk-for-python/).
* Ensure that the IAM Role attached to the Lambda function has a policy with ec2. If you want to create a custom policy, include:
   + ec2:DeleteVolume
   + ec2:DescribeRegions
   + ec2:DescribeVolumes
* Use the usual CloudWatch Logs role for logging.
* A cron job in CloudWatch to invoke the Lambda function at the desired times.

### To set up boto3 for development (Amazon Linux and similar):
```
sudo yum install -y python3 python3-pip python3-setuptools
pip3 install boto3 --user
aws configure [enter your AWS access key and secret key]

python3
>>> import boto3
>>> ec2 = boto3.client('ec2')
>>> response = ec2.run_instances(ImageId='ami-00dc79254d0461090',InstanceType='t2.micro',KeyName='MY KEY',MinCount=1,MaxCount=1)
```

License
---------------
GNU General Public License v3.0
