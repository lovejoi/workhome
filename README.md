# workhome 

Task 1:

You've joined a new and growing startup.

The company wants to build its initial Kubernetes infrastructure on AWS. The team wants to leverage the latest autoscaling capabilities by Karpenter, as well as utilize Graviton instances for better price/performance

They have asked you if you can help create the following:

Terraform code that deploys an EKS cluster (whatever latest version is currently available) into an existing VPC

The terraform code should also deploy Karpenter with node pool(s) that can deploy both x86 and arm64 instances

Include a short readme that explains how to use the Terraform repo and that also demonstrates how an end-user (a developer from the company) can run a pod/deployment on x86 or Graviton instance inside the cluster.

### One of the suggested solutions of Tasks 1 can be find in folder task1


Task2:

One of our clients has multiple GPU-intensive AI workloads that run on EKS.

Their CTO heard there is an option to cut GPU costs by enabling GPU Slicing.

We want to help them optimize their cost efficiency.

Research the topic, and describe how they can enable GPU Slicing on their EKS clusters.

Some of the EKS clusters have Karpenter Autoscaler, they’d like to leverage GPU Slicing on these clusters as well. If this is feasible, please provide instructions on how to implement it.

### One of the suggested solutions for Tasks 2 can be find in folder task2