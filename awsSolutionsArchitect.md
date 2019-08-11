# AWS Solutions Architect Study Notes

## Amazon Recommended FAQ's

- [https://aws.amazon.com/architecture/well-architected/] (Well Architected)
- [https://aws.amazon.com/sqs/faqs/] (S3)
- [https://aws.amazon.com/route53/faqs/] (Route 53)
- [https://aws.amazon.com/ec2/faqs/] (EC2)
- [https://aws.amazon.com/vpc/faqs/] (VPC)
- [https://aws.amazon.com/rds/faqs/] (RDS)
- [https://aws.amazon.com/sqs/faqs/] (SQS)

## Cognito ( Web Identity Federation )

## Kinesis

- 

## API Gateway

- Exposes HTTPS endpoints to define a RESTful API
- Runs efficiently with very low cost
- Front End: Can be passed to Lambda, EC2 or DynamoDB
- Fully managed service to publish maintain and secure API's at any scale
- Click an API that acts as a front door for your apps to access data, biz logic or functionalityfrom your back-end services
- You don't need EC2 instances behind it. You can use it for code running on Lambda functions
- Scales effortlessly, no need to work with auto-scaling groups
- Track and control usage with an API-key
- Throttle requests to prevent attacks
- Connect to cloudwatch to log all requests for monitoring
- Maintain multiple versions of your API. Can use a custom domain name
- Supports AWS Certificate Manager: free SSL/TLS certs
- **API Caching**: Cache your endpoint responses. 

## Cross Origin Resource Sharing

- Cross Origin Resource Sharing: 
- Same Origin Policy: A script in one page can execute on another page if its from the same domain. This prevents one domain from attacking other domains (cross-site scripting XSS attacks)
- CORS: Cross-origin resource sharing is a mechanism that allows restricted resources ( fonts eg ) to be shared from one domain on another domain
- Error: "Origin policy cannot be read at the remote resource?" - **You need to enable CORS on API Gateway**
- CORS enforced by the Client (browser)


## Elastic Transcoder

- Media Transcoder in the cloud
- Coverting media files from original source into different formats that will play on smartphones, tablets, PC's etc
- Provides transcoding presets for popular output formats
- A Cloud Guru uses this with a lambda function to generate their videos since 2015

## SQS 

- Pull based, not pushed based like SNS
- 256kb in size
- Messages can be kept in queue from 1 min to 14 days
- Visibility time out: time message is invisible in the SQS queue after reader picks up message. This allows a message on a dead to be visible again after an amount of time and picked up by another EC2 instance. 12 hrs maximum.
- Guarantees processed at least once
- SQS long polling doesnt return response until message arrives in queue. Way to save money also. 

## SNS (Simple Notification System)

- Both SNS and SQS are messaging systems but one is push ( SNS ) and one is pull/poll ( SQS )
- Inexpensive, flexible message delivery, simple API with easy integration
- Push notifications, no polling ( Apple, google, Android, Fire OS, Windows )
- SMS Text, Email, SQS, or any HTTP endpoint
- Group multiple recipients using topics
- A topic is an "access point" 
- A billing alert is a "billing topic"
- You can group together multiple endpoint types into one topic
- Stored redudantly across multiple AZ's


## SWF ( Simple WorkFlow Service )

- Coordinates work across distributed application components. 
- Task coordinator performed by executable code, web service calls, human actions and scripts
- Remember how Amazon uses it, in a Warehouse with human interaction
- Workflow executions can last up to 1 year
- Task-oriented API, whereas SQS is a message-oriented API
- Keeps track of all tasks and events in an application
- Assigned once and never duplicated
- SWF Actors: Workflow starters ( an app that can initiate a workflow ) Deciders: ( Controls flow of activity tasks in workflow execution) Activity Workers: (Carrys out the activity tasks)

##  Load Balancers

- Resiliency: Ability of a system to self heal after damage or an event
- Scaling Up: Adding more RAM or buffing up the resources
- Scaling Out: More of same resource working in parallel
- Sticky Sessions: sends a user to an ec2 instance despite a load balancer
- No Cross Zone Load Balancing: Cannot send traffic to another AZ
- With Cross Zone Load Balancing:  Can send traffic across other Availability Zones
- Path Patterns: Allow you to direct traffic to different EC2 instances based on the URL contained in the request


## VPC Endpoints

- Interface Endpoints ( Elastic Network Interface ) ENI - 
- Gateway Endpoints ( S3 and Dynamo supported ) 
- Does not require an internet gateway, nat device

## VPC Flow Logs

- Captures information for CloudWatch
- Created at VPC, Subnet and Network Interface Levels
- Cannot tag a flowlog
- Cannot associate different IAM role once created
- Not all IP traffic is monitored

## NAT's versus Bastions

- Why use Bastions? You want to SSH/RDP into one of your private subnet EC2 instances
- Why use Nat Gateways/Instances? To provide internet traffic to EC2 instances on private subnets
- Network computer designed to withstand attacks
- Cannot use a NAT Gateway as a Bastion host

## Direct Connect

- On premises to AWS connection via dedicated lines

## Application Load Balancers 

- Minimum of 2 subnets required!!

## VPC's NAT Instances and Gateways

- NAT Instance - Terribly out of date, being phased out
- NAT Instance - Prone to bottlenecking, requires larger instance for more nodes to connect to
- NAT Instance - Individuals, single EC2 instance, must disable source/destination check on instance
- NAT Instance - Personal gateway for private subnets, single point of failure if terminated, blackhole 
- NAT Gateways - 9x out of 10 you're using these. Highly available, spread across multiple AZ's
- NAT Gateways - Allows your private subnets to communicate out to the internet without becoming public 
- NAT Gateways - Only one per AZ, preferred by Enterprise, 5Gbps and scales up to 45Gbps
- NAT Gateways - No need to patch, not assoc with Sec Groups, auto assigned Public IP Address
- NAT Gateways - Always create multiple NAT Gateway in each AZ and configure routing to ensure they use the GW in their AZ

## Network Access Control Lists ( NACL's)

- When created, everything DENIED by default
- When creating NACL's, all inbound/outbound traffic is denied by default
- When creating, if you don't associate a subnet, the default is specified
- You can block IP's with NACL's, you cannot with Security Groups
- You can associate a NACL with multiple subnets
- A subnet can only be associated with NACL at a time
- Numbered list of rules, in order of precedence
- Stateless, inbound does not mean same rules for outbound


## DNS and Route 53

### Routing Policies

- Simple ( one record with multiple IP addresses )
- Simple ( all values returned in random order )
- Weighted ( 20% can go to one Region, 80% to another Region )

- SOA ( Start of Authority ) record contains the NS records
- A record stands for Address, used to translate a domain to an IP address
- C record ( Canonical Name ) resolves one domain name to another domain name
- Alias records are similar to a CNAME record however a CNAME cant be used for a naked domain name (w/out www)
- TTL ( Time to Live ) is the length that a DNS record is cached in seconds
- 48 hours default TTL cached length
- ELB's do not have pre-defined IPV4 addresses
- Given the choice, always choose an Alias over a CNAME
- PTR Record is the reverse of an A record

## RDS

- RDS runs on virtual machines, you cannot log into these OS's 
- You cannot patch or maintain these systems ( you can with EC2, that's your responsibility )
- RDS is NOT serverless ( Aurora is the exception to the rule )
- Aurora Serverless is Serverless

## Athena

- Interactive query service that makes it easy to analyze data
- Works with JSON, Apache Parquet and Apache ORC data formats

### Read Replicas

- Read Replica's can be Multi-AZ
- Can be used to increase performance
- Must have backups turned on
- Can be in different regions
- Can be Aurora or Mysql
- Can be promoted to Master but this will break Read Replica

### RDS Backups

- Two types of database backups ( Automated Backups and Database Snapshots )
- Encryption at rest supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB and Aurora
- Encryption is done using the AWS Key Management System (KMS)
- Once RDS instance is encryped, the data stored at rest in underlying storage is also encrypted ( automated backups, read replicas and snapshots )

### Redshift

- 1 day retention period backups by default
- max retention period is 35 days
- always maintains at least 3 copies of your data
- can also async replicate data to s3 in another region for DR

### Aurora

- 10 gig increments
- 2 copies of data in each AZ w/ minimum 3 AZ's ( 6 copies of your data )
- extremely high available
- storage is self healing, data blocks continiously scanned for errors
- backups en

# EC2 Notes

## EC2 Placement Groups

- Clustered placement groups - low latency, high throughput, cant span AZ's, req's unique name
- Spread placement group - separated away from each other, can span AZ's, req's unique name

Clustered | Spread
------------ | -------------
Extremely Low Latency | Distinct hardware
High Throughput | Critical instances separate
Cannot span AZ's | Can span AZ's 
Requires unique name | Requires unique name

## EC2 Snapshots

- Snapshots of encrypted volumes are encrypted automatically
- Volumes restored from encrypted snapshots are encrypted automatically
- 
- To move an EC2 volument from one AZ to another, take a snapshot of it, create an AMI from the snapshot and then use the AMI to launch the EC2 instance in the new AZ
- To move an EC2 volume from one region to another, take a snapshot of it, create an AMI from the snapshot and then copy the AMI from one region to the other. Then use the copied AMI to launch the new EC2 instance in the new region.

## EC2 Instance Data

- Instance data can be retrieved with ( such as public ip )

        curl http://169.254.169.254/latest/user-data/
        curl http://169.254.169.254/latest/meta-data/


## EC2 Notes

- When initially launching an EC2 Instance, the root drive is Not Encrypted
- Termination protection is turned off by default
- Security Group changes take effect immediately
- You can have any number of EC2 instances attached to security groups and vice versa
- Default action is root EBS volume will be deleted when instance is terminated 
- When you make a change to a security group, that change takes effect immediately
- Security Groups are Stateful, NACL's are Stateless
- All Outbound traffic is allowed even if deleted because Security Groups are stateful
- Security Groups cant block ports or individual IP addresses ( But everything is blocked by default )


# S3

## S3 Notes

- Key, Value, Version ID, Metadata, Subresources ( ACL , Torrent )
- Unlimited storage
- Files can be from 0 Bytes to 5TB
- Names must be unique globally
- Object based
- Files stored in buckets ( folders )
- 200 status code for successful uploads
- You can turn on MFA delete
- Not suitable for databases or operating systems ( block based storage for those )

## S3 Consistency Model

- Read after Write consistency for PUTS of new Objects ( As soon as you create a new object, you'll be able to read that object )
- Eventual Consistency for overwrite PUTS and DELETES ( If you update an object or delete an object, you'll get eventual consistency. So you'll get the older object or you might still see the deleted file, but if you wait a second, its going to be consistent )

## S3 Tiered Storage Levels

- S3 Standard, 99.99% availability, 11 9's durability
- S3- IA ( Infrequently Accessed ) Lower fee than S3 but charged retrieval fee
- S3 One Zone - IA , do not require multiple availability zone data resilience - 
- S3 - Intelligent Tiering ( Optimizes costs by moving data to lower tiers automatically )
- S3 Glacier - Data archive
- S3 Glacier Deep Archive - retrieval time of 12 hrs is acceptable ( Lowest cost! )

## Read the S3 FAQ's before taking the Exam!

### Encryption in Transit is achieved by:

- SSL/TLS

### Encryption At Rest (Server Side) is achieved by:

- S3 Managed Keys - SSE - S3
- AWS Key Management Service, Managed Keys - SSE-KMS ( cooperative encryption )
- Server Side Encryption with Customer provided Keys - SSE-C

## S3 Versioning and File Permissions

- Stores all version of an object, even writes and deletes
- Versioning once enabled cannot be disabled, only suspended

## S3 Cross Region Replication

- Versioning must be enabled on both the source and destination buckets
- Regions must be unique
- Files in an existing bucket are not replicated automatically
- All subsequent updated files will be replciated automatically
- Delete markers are not replicated
- Deleting individual versions or delete markers will not be replicated

## S3 Transfer Acceleration

- You upload file to a Cloudfront Edge Network location
- File is sent along backbone to your S3 bucket in your region
- Transfer acceleration tool lets you see how much faster it is

## CloudFront

- Origin ( Source of all the files that the CDN distributes, ie: S3 Bucket, EC2 Instance, ELB, Route53 )
- Really good performance 
- Typically used for Websites
- Used for Media Streaming
- Web Distribution ( Typically used for Websites )
- RMTP ( Used for Streaming )
- You can also write to Edge Locations
- You can clear/invalidate cached objects ( But you will be charged )

## Snowball & Snowball Edge

- Import to and from S3

## EBS 

- General Purpose SSD ( gp2 )
- Provisioned IOPS SSD ( io1 )
- 


## Extra

- Amazon Quick Starts https://aws.amazon.com/quickstart/
