# Managing Kubernetes on AWS

## 3 Popular Methods

- Use Amazon EKS to manage your cluster
- Use Kops to manage your cluster
- Manually set up everything on EC2 instances

## Amazon EKS ( Elastic Container Service for Kubernetes ) 

- Highly available, scalable and secure Kubernetes service
- Fairly complicated setup 
- Control plane is completely managed
- Requires AWS Cli and aws-iam-authenticator
- Tools like CloudFormation and Terraform make setting up EKS easier
- https://docs.aws.amazon.com/eks/latest/userguide/getting-started.html

# Kops ( Kubernetes Operations ) 

- CLI tool for Production Grade K8s Installation, Upgrades and Management
- Installed locally alongside kubectl
- run kops create cluster
- creates your master nodes as EC2 instances 

## Docs

- https://helm.sh/docs/
- 
