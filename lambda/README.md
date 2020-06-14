
## Automating AWS with Lambda, Python, and Boto3

Lambda is a serverless computing platform
  - Serverless means you can run code without provisioning or managing server
  - Pay only what you use
  - Managed by AWS, highly available, fault tolerant, scalable, elastic & cost effective
 
 Working with Lambda
  - BY default AWS gives very less permission to newly created lambda function, only cloudwatch logs
  - Lambda functions are triggered by events
  
 Configuring EC2 instance on AWS
  - Create new EC2 machine by choosing AMI 2 (which has AWS CLI pre installed)
  - Connect to EC2 machine using ssh
      ```
      $ ssh -i <.pem file> ec2-user@<IPAddress>
      ```
  - Update the instance
      $ sudo yum update
  - Install Python
      $ sudo yum install -y python3-pip python3 python3-setuptools    # -y for automatically accept any prompts
  - Install boto
      $ pip3 install boto3 --user    # user flag to make sure library install on user space
  - Use python3 for working with python 3.7
  - Configure AWS CLI
      $ aws configure
    It will prompt for AWS Access Key ID, secret access key, default region name, default output format (json)
  - To test the setup use command
      $ aws sts get-caller-identity
  - To test boto3 setup, open python console and use command
      $ import boto3
  
      




