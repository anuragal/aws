### Steps to create EC2 instance using Lambda

1.  Browse to Lambda service using AWS management console
2.  Click Create a function
3.  Choose Author from scratch and use the following settings:
      ```
      Name: TestCreateEC2
      Runtime: Python 3.7
      Role: Create a custom role
      ```
4. Expand & Set role to `Create a new role with basic Lambda permissions`. Copy the execution role name that appears in the bottom with blue backgroud
5. Click on Create
6. Navigate to IAM, search for and select your newly created role
7. Edit the policy to replace its existing policy with below JSON
  ```json
      {
        "Version": "2012-10-17",
        "Statement": [{
            "Effect": "Allow",
            "Action": [
              "logs:CreateLogGroup",
              "logs:CreateLogStream",
              "logs:PutLogEvents"
            ],
            "Resource": "arn:aws:logs:*:*:*"
          },
          {
            "Action": [
              "ec2:RunInstances"
            ],
            "Effect": "Allow",
            "Resource": "*"
          }
        ]
      }
  ```
  Above IAM role has default policy + new policy which allow running EC2 instances
8.  Go back to the Lambda console, scroll to the Function code section and paste the below Python source code
  ```python
      import os
      import boto3

      ec2 = boto3.resource('ec2')

      def lambda_handler(event, context):
          instance = ec2.create_instances(
              ImageId = <AMI_ID>,
              InstanceType = 't2.micro',
              KeyName = <key-pair-name>,
              SubnetId = <subnetid-where-EC2-tobe-created>,
              MaxCount=1,
              MinCount=1
          )
          print("EC2 instance created with ID: ", instance[0].id)
  ```
9. Save the Lambda function
10. Click Test & create test event with {} block
11. Click Create
12. Click Test again
13. GO to either CloudWatch or EC2 to see whether instance is created or not
