# AWS Services Overview

This document provides a brief overview of key AWS services with simple examples.

## 1. **EC2 (Elastic Compute Cloud)**
- **What it does**: Provides virtual servers (instances) in the cloud.
- **Example**: Launch a Linux server to host a website.
  ```bash
  aws ec2 run-instances --image-id ami-0abcdef1234567890 --instance-type t2.micro
  ```

## 2. **S3 (Simple Storage Service)**
- **What it does**: Stores and retrieves any amount of data (files, images, etc.).
- **Example**: Upload a file to an S3 bucket.
  ```bash
  aws s3 cp myfile.txt s3://my-bucket/
  ```

## 3. **Lambda**
- **What it does**: Runs code without managing servers (serverless).
- **Example**: Create a Lambda function that logs "Hello, World!".
  ```python
  def lambda_handler(event, context):
      print("Hello, World!")
  ```

## 4. **RDS (Relational Database Service)**
- **What it does**: Managed relational databases (MySQL, PostgreSQL, etc.).
- **Example**: Launch a MySQL database.
  ```bash
  aws rds create-db-instance --db-instance-identifier mydb --engine mysql --db-instance-class db.t2.micro --allocated-storage 20
  ```

## 5. **IAM (Identity and Access Management)**
- **What it does**: Manages user access and permissions.
- **Example**: Create a new IAM user.
  ```bash
  aws iam create-user --user-name MyUser
  ```

## 6. **CloudFront**
- **What it does**: Content delivery network (CDN) for fast content delivery.
- **Example**: Create a CloudFront distribution for an S3 bucket.
  ```bash
  aws cloudfront create-distribution --origin-domain-name my-bucket.s3.amazonaws.com
  ```

## 7. **DynamoDB**
- **What it does**: NoSQL database for high-performance applications.
- **Example**: Create a DynamoDB table.
  ```bash
  aws dynamodb create-table --table-name MyTable --attribute-definitions AttributeName=ID,AttributeType=N --key-schema AttributeName=ID,KeyType=HASH --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5
  ```

## 8. **SNS (Simple Notification Service)**
- **What it does**: Sends notifications (email, SMS, etc.).
- **Example**: Send an SMS notification.
  ```bash
  aws sns publish --phone-number +1234567890 --message "Hello from AWS SNS!"
  ```

## 9. **SQS (Simple Queue Service)**
- **What it does**: Message queuing for decoupling applications.
- **Example**: Create a message queue.
  ```bash
  aws sqs create-queue --queue-name MyQueue
  ```

## 10. **CloudWatch**
- **What it does**: Monitors AWS resources and applications.
- **Example**: Create a CloudWatch alarm for high CPU usage.
  ```bash
  aws cloudwatch put-metric-alarm --alarm-name HighCPU --metric-name CPUUtilization --namespace AWS/EC2 --statistic Average --period 300 --threshold 80 --comparison-operator GreaterThanOrEqualToThreshold --dimensions Name=InstanceId,Value=i-1234567890abcdef0 --evaluation-periods 2 --alarm-actions arn:aws:sns:us-east-1:123456789012:MyTopic
  ```

## 11. **VPC (Virtual Private Cloud)**
- **What it does**: Isolated cloud network for your resources.
- **Example**: Create a VPC.
  ```bash
  aws ec2 create-vpc --cidr-block 10.0.0.0/16
  ```

## 12. **Route 53**
- **What it does**: Domain name system (DNS) service.
- **Example**: Register a domain.
  ```bash
  aws route53domains register-domain --domain-name example.com --duration-in-years 1 --admin-contact {...} --registrant-contact {...} --tech-contact {...}
  ```

## 13. **Elastic Beanstalk**
- **What it does**: Deploys and manages web applications.
- **Example**: Deploy a Python app.
  ```bash
  aws elasticbeanstalk create-application --application-name MyApp
  ```

## 14. **ECS (Elastic Container Service)**
- **What it does**: Runs Docker containers.
- **Example**: Create an ECS cluster.
  ```bash
  aws ecs create-cluster --cluster-name MyCluster
  ```

## 15. **Kinesis**
- **What it does**: Processes real-time data streams.
- **Example**: Create a Kinesis stream.
  ```bash
  aws kinesis create-stream --stream-name MyStream --shard-count 1
  ```

## 16. **Glue**
- **What it does**: ETL (Extract, Transform, Load) service for data preparation.
- **Example**: Create a Glue job.
  ```bash
  aws glue create-job --name MyJob --role AWSGlueServiceRole --command '{"Name": "my-etl-job"}'
  ```

## 17. **Redshift**
- **What it does**: Data warehousing for analytics.
- **Example**: Launch a Redshift cluster.
  ```bash
  aws redshift create-cluster --cluster-identifier mycluster --node-type dc2.large --master-username admin --master-user-password Password123 --cluster-type single-node
  ```

## 18. **Step Functions**
- **What it does**: Coordinates serverless workflows.
- **Example**: Create a state machine.
  ```bash
  aws stepfunctions create-state-machine --name MyStateMachine --definition '{"StartAt": "HelloWorld", "States": {"HelloWorld": {"Type": "Pass", "Result": "Hello, World!", "End": true}}}' --role-arn arn:aws:iam::123456789012:role/MyRole
  ```

## 19. **API Gateway**
- **What it does**: Creates and manages APIs.
- **Example**: Create a REST API.
  ```bash
  aws apigateway create-rest-api --name MyAPI
  ```

## 20. **Secrets Manager**
- **What it does**: Stores and manages secrets (passwords, API keys, etc.).
- **Example**: Store a secret.
  ```bash
  aws secretsmanager create-secret --name MySecret --secret-string '{"username":"admin","password":"Password123"}'
  ```

---

### Notes:
- Replace placeholders (e.g., `my-bucket`, `MyUser`, `example.com`) with your actual values.
- Ensure you have the AWS CLI installed and configured (`aws configure`).