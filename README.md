# eks-dotnetcore

Step #1 create EKS cluster

eksctl create cluster \
--name prod \
--version 1.16 \
--region us-west-2 \
--fargate

Step #2 Create a Fargate pod execution role

Open the IAM console at https://console.aws.amazon.com/iam/. 
Choose Roles, then Create role. 
Choose EKS from the list of services, EKS - Fargate pod for your use case, and then Next: Permissions. 
Choose Next: Tags. 
(Optional) Add metadata to the role by attaching tags as key–value pairs. For more information about using tags in IAM, see Tagging IAM Entities in the IAM User Guide. 
Choose Next: Review. 
For Role name, enter a unique name for your role, such as AmazonEKSFargatePodExecutionRole, then choose Create role. 

Step #3 Create Fargate Profile

eksctl create fargateprofile --cluster prod --name prodprofile --namespace prod --labels name=prod

