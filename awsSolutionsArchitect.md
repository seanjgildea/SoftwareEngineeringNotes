# AWS Solutions Architect Study Notes

## Amazon Recommended FAQ's

- (Well Architected)[https://aws.amazon.com/architecture/well-architected/]
- (S3)[https://aws.amazon.com/sqs/faqs/]
- (Route 53)[https://aws.amazon.com/route53/faqs/]
- (EC2)[https://aws.amazon.com/ec2/faqs/]
- (VPC)[https://aws.amazon.com/vpc/faqs/]
- (RDS)[https://aws.amazon.com/rds/faqs/]
- (SQS)[https://aws.amazon.com/sqs/faqs/]

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
