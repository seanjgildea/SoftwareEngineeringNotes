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

# Exam API Commands

- GetSessionToken: used to call an API where he can submit the MFA code associated with his MFA device
- AssumeRoleWithWebIdentity: returns a set of temporary security credentials for federated users
- AssumeRoleWithSAML: returns a set of temporary security credentials for users who have been authenticated via a SAML resp
- GetFederationToken: Does not support MFA

# Lambda

- It was all about the functionality of the service itself. Understand execution times, the concept of concurrent executions, and how Lambda can be triggered.
- IAM, CodeDeploy, CloudFormation. Particularly, how to deploy a lambda function using these services
- Lambda code size limits
- Lambda (used heavily in the exam) deployment using CloudFormation
- How to schedule a lambda function
- Understand Swagger with Lambda and SAM/Cfn
- SWAGGER and how its used to deploy a serverless framework
- Various Lambda configurations: VPC Integration, RAM, Concurrency Execution
- Cloudwatch logs help debug lambda function output by default
- Cloudwatch automatically monitors functions on your behalf, reporting metrics like total request rates. 
- When a lambda alias ARN is used in the notification config & a new version of a lambda function is created, you need to update the Alias ARN pointing to the new function.
- Avoid Recursion in Lambda functions to prevent 
- Canary deployment preference shifts traffic in 2 intervals, x amount in the first interval and the remaining traffic in the 2nd interval of time
- Lambda@Edge is an extension that lets you execute functions that customize the content that CloudFront delivers


# CloudFormation 

- CloudFormation does show up in the exam including intrinsic functions, mappings,
- huge topic, templates, nested, SAM
- Understand differences and most importantly when to use them.
- Swagger - really was mentioned in passing, but I also had 2 questions, Swagger + cfn-init using CloudFormation - go figure.

# DynamoDB / Elasticache

- dynamodb:LeadingKeys = fine grained access control IAM condition parameter where partition key value matches their user ID
- LSI vs GSI Indexes
  - Local Secondary Index (LSI) = An index that has the same partition key as the base table, but a different sort key.
  - Global Secondary Index (GSI) = An index with a partition key and a sort key that can be different from those on the base table
  - The primary key of a Local Secondary Index must be composite (partition key and sort key).
  - The primary key of a Global Secondary Index can be either simple (partition key) or composite (partition key and sort key).
  - A global secondary index lets you query over the entire table, across all partitions. LSI: Only single partition
  - When you query a LSI, you can choose either eventual consistency or strong consistency. GSI: Only eventual consistency
  - Global secondary indexes inherit the read/write capacity mode from the base table
  - When you query a local secondary index, the number of read capacity units consumed depends on how the data is accessed. An index query can use either eventually consistent or strongly consistent reads depending on the value of ConsistentRead
- DynamoDB DAX
  - Clustered in-memory cache for Eventually Consistent reads ONLY
  - For read-heavy and bursty workloads ( Black Friday ) 
  - write-through caching service 
  - cache misses are retrieved via GETITEM operation 
  - DAX bad for write intensive apps and Strongly Consistent reads
- DynamoDB Scan vs Query
  - Avoid scan operations, use Query, Get or BatchGetItem APIs
  - Scan dumps entire table then filters on attribute
  - Query on Partition Key (Primary Key)
  - Pagesize can reduce impact (fewer read operations)
  - Parallel scan divides into segments scanning each in parallel
  - Use ProjectExpression parameter to refine a scan result
  - ScanIndexForward=false reverses order of queries only
- Elasticache: Lazy Loading vs Write Through
  - Cache miss penalty: Lazy Loading: Initial request, query db, write to cache
  - Write through: Update cache whenever change to db. Data never stale but cache penalty
- DynamoDB has a TTL attribute to define when items in a table expire / auto deleted
- DynamoDB GSI and LSI (including its RCU and WCU relationship with the base table)
- DynamoDB offers fully managed Encryption at rest

# CodePipeline, CodeDeploy, CodeCommit, CodeBuild, Codestar

- Codedeploy uses appspec files for configuration (specifies lambda function version to deploy)
- CodePipeline creates an S3 artifact bucket and default SSE-KMS keys. Data is encrypted at rest. 
- Client-side encryption with KMS and You needed to know the sequence
- Plenty of questions on the different services. Definitely know what role each service plays
- Know SAM and examples of build and deploy scripts
- create-project / update-project commands run a build with a source location of the build
- Codestar is used for creating, managing and working with software development projects using templates. 

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

# Elastic Beanstalk

- You can set configuration options in saved configurations/files to change things like instance type upon environment creation.

# Cloudwatch, Cloudtrail and AWS Config

- What can trigger an alarm, metric or log?
- If you set an alarm on a high-resolution metric, you can specify a 10 or 30 seconds period or a regular alarm with a period of any multiple of 60 seconds

# API Gateway

- Some tricky questions on API Gateway and lambda especially around rate limiting
- API Gateway Cache Invalidation
- myapi?name=test vs. myapi/test - how to get the API to handle both cases Very strange and complicated use cases.
- Extremely heavy in this, with lots of things about authorization, a bit of caching, and plenty about how resources (particularly Lambda) are invoked. 
- WAF and Resource Policies can both limit or deny specific IP addresses from accessing API Gateway
- Stage variables are name-value pairs that you define as config attributes associated with a deployment stage of an API. They act like env vars and can be used in your API setup and mapping templates.

# Cognito / Cognito Sync

- Two questions on AWS Cognito Syncing and data management.
- Cognito was included in many questions
- Remember that Cognito is the preferred Federation method for mobile.

# KMS

### Envelope Encryption
- unencrypted data is encrypted using plaintext Data key. Data key is further encrypted using plaintext master key. Plaintext master key is securely stored in KMS and known as Customer Master Keys
- 

# IAM 

- To assume a role, an application calls the AWS STS AssumeRole API operation and passes the ARN of the role to use. 

# Various / Memcached / Redis

- Systems Manager Parameter Store - Know how it works and what it can do for you
- know how to use S3 bucket policy to prevent uploads of unencrypted objects.
- Use Redis for Gaming Leaderboards due to its "sorted sets"


# Whitepapers to Study

[https://docs.aws.amazon.com/xray/latest/devguide/xray-api-segmentdocuments.html]

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html#GSI.ThroughputConsiderations

https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html

https://aws.amazon.com/premiumsupport/knowledge-center/authenticate-mfa-cli/

https://docs.aws.amazon.com/streams/latest/dev/kinesis-record-processor-scaling.html

https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html#GSI.ThroughputConsiderations

https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-migrate-repository-existing.html

https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/publishingMetrics.html
