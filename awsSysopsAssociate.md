# SysOps Associate Exam


## EC2 
- Changed the Instance type of an EC2 and did not lose any data, watched the memory increase via CLI
- Placement Groups ( Cluster, Spread, Partition )
  - How to add an instance to one on creation
- Termination on shutdown and Termination protection
  - We saw how via the CLI, even if termination protection is enabled via console, it is ignored via CLI
- InstanceLimitExceeded Error: resolution -> launch instance in different region or ask for increase of region
- InsufficientInstanceCapacity: resolution -> wait few min, try diff instance type, reduce request number
- Instance Terminates Immediately: 1. EBS volume limit. 2. EBS snapshot corrupt. 3. EBS volume is encrypted/no permissions. 4. AMI image is missing a part. Solution -> show 'state transition reason' from the gear icon
- EC2 SSH Issues:
  - Unprotected Pem File while logging in: resolution -> chmod 400 AWSCourse.pem , was probably 755 permissions
  - Permission Denied: resolution -> check user name 'ec2-user' for linux AMI
  - Completely Times out: resolution -> security group rules are wrong because SSH port rule is not enabled
- EC2 Instance Launch Types:
  - On Demand: billed per second after first minute - no committment
  - Reserved: up to 75% discount compared to on-demand. 1-3 year reservation periods
  - Convertible: up to 54% discount, can change EC2 instance type
  - Scheduled Reserved Instances: launch within time window
  - Spot Instances: up to 90% discount compared to On-Demand. 2 minute notification warning when spot goes above bid. resilient workloads, big data
  - Dedicated Instances: no other customers share your server. no con
  - Dedicated Hosts: book entire physical server - 3 yr reservation period, more expensive. BYOL - strong regulatory needs. 
