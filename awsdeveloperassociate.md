# AWS Developer Associate Notes

- Most of my exam questions are around API Gateway, Lambda, Cognito (not many for S3, SQS and SNS).
- Lambda in almost 70% of questions
- Two words exponential Backoff which was the answer for several services
- GetItem,BatchWriteItem,PutItem,BatchPutitem and several more

# ECS & ECR

- Yes, a huge chunk in my exam, probably 15-20 questions.  They are all about provisioning underlying EC2, what can be done in a task definition, etc. e.g. I got questions about using ALB for dynamic port mapping and where to configure that.

- There were many questions on ECS (single, multi-containers, container agent, task definitions ) 

- Many questions about Elastic Load Balancers, Beanstalk, EC2 and ECS

- What is the correct procedure to remove RDS from Elastic Beanstalk?
  -  Create a saved configuration, download from S3 (in your EBS S3 bucket, go to resources/templates/<your-app-name>/), edit to remove the RDS instance, and re-upload it.
  
- how to force your application to use the EBS DNS

- Beanstalk deployment optimization & Beanstalk with Docker

# Lambda

- It was all about the functionality of the service itself. Understand execution times, the concept of concurrent executions, and how Lambda can be triggered.

- IAM, CodeDeploy, CloudFormation. Particularly, how to deploy a lambda function using these services

- Lambda code size limits

- Lambda (used heavily in the exam) deployment using CloudFormation
 
- How to schedule a lambda function

- Understand Swagger with Lambda and SAM/Cfn

- SWAGGER and how its used to deploy a serverless framework

- Various Lambda configurations: VPC Integration, RAM, Concurrency Execution


# CloudFormation 

- CloudFormation does show up in the exam including intrinsic functions, mappings,

- huge topic, templates, nested, SAM

- Understand differences and most importantly when to use them.

- Swagger - really was mentioned in passing, but I also had 2 questions, Swagger + cfn-init using CloudFormation - go figure.

# DynamoDB

- DynamoDB - several question on throttling and primary table throttling due to secondary index under provisioning

- Comparison between ElasticCache and DynamoDB (DynamoDB was used heavily in the exam)

- DynamoDB Cache Strategy

- DynamoDB Scan vs Query
  - Scan dumps entire table than filters on attribute
  - Query on Partition Key (Primary Key)
  - Pagesize can reduce impact (fewer read operations)
  - Parallel scan divides into segments scanning each in parallel
  - Use ProjectExpression parameter to refine a scan result
  - ScanIndexForward=false reverses order of queries only
  
- DynamoDB GSI and LSI (including its RCU and WCU relationship with the base table)

# CodePipeline, CodeDeploy, CodeCommit, CodeBuild

- Client-side encryption with KMS and You needed to know the sequence

- Plenty of questions on the different services. Definitely know what role each service plays

-  Know SAM and examples of build and deploy scripts

# X-Ray

- Instrumenting your applications with X-Ray

- X-Ray Segment Documents

- X-ray -was seen multiple times during the exam

- Enable active tracing particularly

- how to instrument applications in EC2 for X-ray

- how to instrument applications running in Docker containers in ECS for X-ray etc

# SQS & Kinesis 

- Kinesis Resharding. Remember that each shard is processed by exactly one KCL worker and has exactly one corresponding record processor, so you never need multiple instances to process one shard.

- SQS Dead Letter Queues details

- SQS was covered in detail (FIFO queues etc..)

- When to use SQS and when to use Kinesis Data Stream

- remember which Kinesis service is used for which function


# Cloudwatch, Cloudtrail and AWS Config

- What can trigger an alarm, metric or log?

# API Gateway

-  some tricky questions on API Gateway and lambda especially around rate limiting

- API Gateway Cache Invalidation

- myapi?name=test vs. myapi/test - how to get the API to handle both cases Very strange and complicated use cases.

- Extremely heavy in this, with lots of things about authorization, a bit of caching, and plenty about how resources (particularly Lambda) are invoked. 

# Cognito / Cognito Sync

- Two questions on AWS Cognito Syncing and data management.

- Cognito was included in many questions

- Remember that Cognito is the preferred Federation method for mobile.

# KMS

- Fargate is also briefly explained and his section on KMS

- Gotta watch those lectures. The concept of Customer Master Keys and Envelope Keys were definitely there

# Various

- Systems Manager Parameter Store - Know how it works and what it can do for you

- know how to use S3 bucket policy to prevent uploads of unencrypted objects.

# Whitepapers to Study

XRay [https://docs.aws.amazon.com/xray/latest/devguide/xray-api-segmentdocuments.html]

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html#GSI.ThroughputConsiderations

https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html

https://aws.amazon.com/premiumsupport/knowledge-center/authenticate-mfa-cli/

https://docs.aws.amazon.com/streams/latest/dev/kinesis-record-processor-scaling.html

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html#GSI.ThroughputConsiderations

https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-migrate-repository-existing.html

https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/publishingMetrics.html
