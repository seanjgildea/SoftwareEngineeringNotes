# AWS Developer Associate Notes

# ECS

-  There were many questions on ECS (single, multi-containers, container agent, task definitions ) 

- Many questions about Elastic Load Balancers, Beanstalk, EC2 and ECS

- ElasticBeastalk, Cloudformation Templates, SAM : understand differences and most importantly when to use them.

# DynamoDB

- DynamoDB - several question on throttling and primary table throttling due to secondary index under provisioning

- DynamoDB Cache Strategy

- DynamoDB Scan vs Query
  - Scan dumps entire table than filters on attribute
  - Query on Partition Key (Primary Key)
  - Pagesize can reduce impact (fewer read operations)
  - Parallel scan divides into segments scanning each in parallel
  - Use ProjectExpression parameter to refine a scan result
  - ScanIndexForward=false reverses order of queries only
  
- DynamoDB GSI and LSI (including its RCU and WCU relationship with the base table)

# X-Ray

- Instrumenting your applications with X-Ray

- X-Ray Segment Documents

# SQS & Kinesis 

- Kinesis Resharding. Remember that each shard is processed by exactly one KCL worker and has exactly one corresponding record processor, so you never need multiple instances to process one shard.

- When to use SQS and when to use Kinesis Data Stream

# Lambda

- Understand Swagger with Lambda and SAM/Cfn

- Various Lambda configurations: VPC Integration, RAM, Concurrency Execution

# Cloudwatch, Cloudtrail and AWS Config

- What can trigger an alarm, metric or log?

# API Gateway

- API Gateway Cache Invalidation
