# AWS Solutions Architect Study Notes

# EC2

## EC2 Snapshots

- To move an EC2 volument from one AZ to another, take a snapshot of it, create an AMI from the snapshot and then use the AMI to launch the EC2 instance in the new AZ
- To move an EC2 volume from one region to another, take a snapshot of it, create an AMI from the snapshot and then copy the AMI from one region to the other. Then use the copied AMI to launch the new EC2 instance in the new region.

## EC2 Instance Store vs EBS

- 

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
