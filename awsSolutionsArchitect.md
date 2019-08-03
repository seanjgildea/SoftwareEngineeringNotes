# AWS Solutions Architect Study Notes

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

