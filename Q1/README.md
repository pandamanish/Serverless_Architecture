# Automated Instance Management Using AWS Lambda and Boto3

# Overview

This project demonstrates how to automate the management of EC2 instances using AWS Lambda and Boto3. 
The Lambda function will automatically start or stop EC2 instances based on their tags, making instance management more efficient.

# Objective
The primary goal is to create a Lambda function that stops and starts EC2 instances based on custom tags:
Instances tagged as Auto-Stop will be stopped.
Instances tagged as Auto-Start will be started.

# Prerequisites
An active AWS account.
Familiarity with AWS services such as EC2, Lambda, and IAM.
Access to AWS Management Console.
Basic knowledge of Python and Boto3.

# Steps 
1. EC2 Setup
Launch Two EC2 Instances:
Go to the EC2 Dashboard in the AWS Management Console.
Launch two t2.micro EC2 instances (or any available free-tier instance type).
Assign the following tags to the instances during creation:
Instance 1: Action = Auto-Stop
Instance 2: Action = Auto-Start
Note the Instance IDs for validation after testing.
2. IAM Role for Lambda
Navigate to IAM Dashboard:

Open the AWS IAM dashboard.
Create a Role for Lambda:

Click Roles > Create role.
Choose Lambda as the trusted entity.
Attach Permissions:

Attach the AmazonEC2FullAccess policy to the role. (In production environments, it's recommended to restrict permissions using a custom policy with only the necessary actions.)
Create the Role:

Name the role (e.g., lambda-ec2-management-role) and create it.
3. Create a Lambda Function
Navigate to the AWS Lambda Console:

Open the AWS Lambda dashboard.
Create a New Lambda Function:

Click Create function.
Choose Author from scratch.
Enter the function name (e.g., manage-ec2-instances).
Select Python 3.x as the runtime.
Under Permissions, select the IAM role created in the previous step.

4. Write the Lambda Function Code
  Stop Instances: The function checks for instances tagged Auto-Stop that are running and stops them.
  Start Instances: It looks for instances tagged Auto-Start that are stopped and starts them.
  Logging: The function logs the instance IDs that were stopped or started for easier monitoring.


# Deploy the Function:

Clicked Deploy to save and deploy the function after writing the code.
Manual Invocation:

Created a test event and manually triggerd the Lambda function.
You don't need to pass any specific input, so you can use the default test event.
Verify Results:

Open the EC2 Dashboard.
Ensure the instance tagged as Auto-Stop is now stopped, and the instance tagged as Auto-Start is running.

