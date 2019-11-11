# AWS Developer Associate Notes

- Various Lambda configurations: VPC Integration, RAM, Concurrency Execution

- API Gateway Cache Invalidation

- DynamoDB Cache Strategy

- DynamoDB Scan vs Query
  - Scan dumps entire table than filters on attribute
  - Query on Partition Key (Primary Key)
  - Pagesize can reduce impact (fewer read operations)
  - Parallel scan divides into segments scanning each in parallel
  - Use ProjectExpression parameter to refine a scan result
  - ScanIndexForward=false reverses order of queries only
  
- DynamoDB GSI and LSI (including its RCU and WCU relationship with the base table)

- Instrumenting your applications with X-Ray

- X-Ray Segment Documents

- Kinesis Resharding. Remember that each shard is processed by exactly one KCL worker and has exactly one corresponding record processor, so you never need multiple instances to process one shard.
