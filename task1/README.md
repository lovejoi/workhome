EKS Cluster with Karpenter

This Terraform configuration deploys an Amazon EKS cluster with Karpenter for autoscaling, supporting both x86 and ARM64 (Graviton) instances.

#Steps for start EKS

git clone git@github.com:lovejoi/workhome.git  #clone repo
cd workhome/task1   #change dir for task1
vim terraform.tfvars # updatefile with your variables
vim main.tf     #check vpc and sumbets name  
terraform init     #terraform initialize
terraform plan     #will show plan what cluster will be created
terraform apply    #cluster will be create


aws eks update-kubeconfig --name my-eks-cluster --region us-west-2 #when EKS cluster is created, configure kubectl to work with it by provide cluster name and region from vars 
kubectl cluster-info
kubectl get nodes




#Example of deploy with x86

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-amd64
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nginx-amd64
  template:
    metadata:
      labels:
        app: nginx-amd64
    spec:
      nodeSelector:
        kubernetes.io/arch: amd64
      containers:
      - name: nginx
        image: nginx:latest
--------------------------------
kubectl apply -f nginx-amd64.yaml



#Deploy on Graviton (arm64)

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-arm64
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nginx-arm64
  template:
    metadata:
      labels:
        app: nginx-arm64
    spec:
      nodeSelector:
        kubernetes.io/arch: arm64
      containers:
      - name: nginx
        image: nginx:latest
 
 ----------------------------
kubectl apply -f nginx-arm64.yaml

kubectl get deployments & kubectl get pods -o wide # check status 

terraform destroy # destroy cluster 





