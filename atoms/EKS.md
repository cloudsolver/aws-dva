### Summary of EKS
Elastic Kubernetes Service is a managed service. The most trusted way to start, run, and scale Kubernetes. #AWSService 
### EKS Details
- EKS supports [[EC2]] if you want to deploy worker nodes or Fargate to deploy serverless containers.
- Kubernetes is cloud-agnostic.
- #UseCase Company is already running Kubernetes on-premises and wants to migrate to AWS using Kubernetes.
- Note Types
	- Managed Node Groups
		- [[ASG]] managed by EKS
		- Supports On-Demand or Spot Instances
	- Self-Managed Nodes
		- Nodes created by you and registered to the EKS cluster and managed by an [[ASG]]
		- Pre-built AMI - Amazon EKS Optimized AMI
		- Supports On-demand or Spot instances
	- AWS [[Fargate]]
		- No nodes needed.
- EKS Data Volumes
	- Specify `StorageClass` manifest on your EKS cluster
	- Leverages a Container Storage Interface ([[CSI]]) compliant driver
	- Support for EBS, EFS (works with Fargate for EKS), FSx for Lustre, FSx for NetApp ONTAP.
- Monitoring with [[CloudWatch]] Container Insights -  configure in the existing EKS cluster. There is no agent to run because there is no access to instances. 
#### References for EKS
1. https://aws.amazon.com/eks/

---
Created on 2023-03-11 21:31