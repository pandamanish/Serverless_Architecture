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
Launched Two EC2 Instances:
Gone to the EC2 Dashboard in the AWS Management Console.
Launched two t2.micro EC2 instances (or any available free-tier instance type).
Assigned the following tags to the instances during creation:
Instance 1: Action = Auto-Stop
Instance 2: Action = Auto-Start
Note the Instance IDs for validation after testing.
![Alt text](Q1/Auto_Start.PNG)
![Alt text](Q1/Auto_stop_setup.PNG)

2. Create a Lambda Function

Navigated to the AWS Lambda Console:
Opened the AWS Lambda dashboard.

Created a New Lambda Function:
Clicked on Create function.
Choosen Author from scratch.
Entered the function name.(manish_lambda_fun)
Selected Python 3.12 as the runtime.
Under Permissions, selected one of the existing IAM role created.
And then created the function.

![Alt text](Q1/AWS_Lambda.PNG)

3. Written the Lambda Function Code which will have these below features.
  Stop Instances: The function checks for instances tagged Auto-Stop that are running and stops them.
  Start Instances: It looks for instances tagged Auto-Start that are stopped and starts them.
  Logging: The function logs the instance IDs that were stopped or started for easier monitoring.


# Deploy the Function:

Clicked Deploy to save and deploy the function after writing the code.

Manual Invocation:
Created a test event and manually triggerd the Lambda function.
Didn't need to pass any specific input, so I can use the default test event.

Verifed Results:
Opened the EC2 Dashboard.
Ensured the instance tagged as Auto-Stop is now stopped, and the instance tagged as Auto-Start is running.
![Alt text](Q1/Auto_Start_output.PNG)
![Alt text](Q1/Auto_stop.PNG)
