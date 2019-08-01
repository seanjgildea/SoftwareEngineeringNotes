[<< Back to Table of Contents](README.md)

## AWS AutoScaling via CloudWatch

- Auto Scaling is especially valuable in environments with fluctuating performance requirements
- This allows you to maintain performance and minimize cost
- Best of all, this process can scale out 2 instances in the middle of the night while you are sleeping

## Route 53

- DNS Service ( Route endusers to endpoints )
- Domain registration, global, highly available DNS ( both IPv4 and IPv6 )
- Public and private DNS names with multiple routing algorithms

## AWS Code Pipeline

- (Source ) AWS CodeCommit - Git
- (Build) AWS CodeBuild 
- (Production) AWS CodeDeploy
- (Monitoring) AWS CodeWatch / AWS X-RAY

## AWS Elastic Beanstalk

- Simply upload your code and Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, auto-scaling to application health monitoring. 
- AWS Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications and services 
- Elastic Beanstalk automatically scales your application up and down based on your application's specific need using easily adjustable Auto Scaling settings. For example, you can use CPU utilization metrics to trigger Auto Scaling actions. With Elastic Beanstalk, your application can handle peaks in workload or traffic while minimizing your costs.

## Deployment and Maintenance

- AWS Elastic Beanstalk - Deploy code into the cloud
- AWS OpsWorks - Manage Infrastructure
- AWS CloudFormation - Lets you define the deployment and maintenance 

## AWS EBS ( Elastic Block Store ) 

- Mission critical performance 
- Database focused storage into the Petabytes
- Ability to store snapshots to S3

## AWS CodeDeploy

- Detects problems on first deployed instance and prevents rollout on further EC2 instances

## AWS CodeBuild

- Terraform AWS resources
- Smoke Tests 
- Failures result in Slack notifications via CircleCI built in notifications

## Questions

- How can I get mastery in AWS?
- What certifications exist for AWS?

## Deployment Tips

- Trigger pipeline on every push
- Run deploy job only on master

## Other Cloud Tools

- Ansible
- Packer
- CloudFormation
- ELK
- Nexus

## AWS Certifications

- https://aws.amazon.com/certification/

- Cloud Practitioner
- https://aws.amazon.com/training/course-descriptions/cloud-practitioner-essentials/
- https://aws.amazon.com/certification/certification-prep/

- Practice Tests
- https://www.awsapprentice.com/

[<< Back to Table of Contents](README.md)
