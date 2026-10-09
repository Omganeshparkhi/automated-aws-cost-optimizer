     # Automated AWS Cost Optimizer

## 1. Project Objective
Automatically identify running EC2 instances tagged `Environment=Development` and stop them to reduce unnecessary AWS costs.

## 2. AWS Services Used
- AWS Lambda
- Amazon EC2
- AWS IAM
- Amazon CloudWatch
- Boto3 (Python SDK)

## 3. Architecture / Workflow
1. Lambda searches for running EC2 instances.
2. It checks the `Environment=Development` tag.
3. With `DRY_RUN=true`, it reports the action without stopping the instance.
4. With `DRY_RUN=false`, it requests the instance to stop.
5. CloudWatch stores execution logs.

**Workflow:** Lambda → EC2 → Tag Filtering → Dry Run / Stop Action → CloudWatch Logs

## 4. Implementation Steps
1. Created an EC2 instance named `CostOptimizer-Dev`.
2. Added the tag `Environment=Development`.
3. Configured IAM permissions.
4. Created the Lambda function `AutomatedCostoptimizer`.
5. Tested the function in Dry Run mode.
6. Executed the stop action and verified the EC2 instance state.
7. Checked execution logs in CloudWatch.

## 5. Screenshots

### 1. Lambda Dry Run Test
![Lambda Dry Run Test](images/lambda-dry-run-test.png)

### 2. Lambda Dry Run False Test
![Lambda Dry Run False Test](images/lambda-dry-run-falsetest.png)

### 3. EC2 Instance Stopped
![EC2 Instance Stopped](images/ec2-stopped.png)

### 4. CloudWatch Logs
![CloudWatch Logs](images/cloudwatch-logs.png)

## 6. How to Run / Deploy
1. Create an EC2 instance with the tag `Environment=Development`.
2. Configure the Lambda execution role with required permissions.
3. Deploy the Python code to Lambda.
4. Set `DRY_RUN=true` and test safely.
5. Verify the target instance before setting `DRY_RUN=false`.
6. Check the EC2 state and CloudWatch logs.

**Safety:** Use `DRY_RUN=true` first. Set it to `false` only after verifying the target instance.

## 7. Key Learnings
- AWS Lambda automation using Python and Boto3.
- EC2 filtering using tags and instance states.
- IAM permissions.
- Safe testing using Dry Run mode.
- Monitoring with CloudWatch Logs.      
