\# Day 10 – Kubernetes \& Amazon EKS Practice



\## 📌 Overview



Today I continued my \*\*Kubernetes learning\*\* and practiced the fundamentals of \*\*Amazon Elastic Kubernetes Service (EKS)\*\*.



\## 🛠️ Topics Covered



\* Practiced Kubernetes using Minikube

\* Started and managed a Kubernetes cluster

\* Checked Pods, Deployments, and Services

\* Exposed an Nginx Deployment using NodePort

\* Inspected Pod details using `kubectl describe`

\* Accessed the running container using `kubectl exec`

\* Learned about Amazon EKS

\* Learned how to create an EKS cluster using AWS

\* Learned about EKS Node Groups

\* Understood the role of VPCs and Subnets in EKS

\* Learned how to connect to EKS using AWS CLI and `kubectl`

\* Learned how to deploy an Nginx application on EKS

\* Learned how to expose applications using a LoadBalancer Service



\## 💻 Commands Practiced



```bash

minikube start



minikube kubectl -- get svc



minikube kubectl -- get pods



minikube kubectl -- expose deployment nginxdeploy --type=NodePort --port=80



minikube kubectl -- get svc



minikube kubectl -- describe pod nginxdeploy-6c997dd56f-7tg26



minikube service nginxdeploy



minikube ip



minikube kubectl -- get deploy



minikube kubectl -- get pods



minikube kubectl -- exec -it nginxdeploy-6c997dd56f-7tg26 -- /bin/bash

```



\## ☁️ Amazon EKS



I learned the basic workflow of deploying applications on Amazon EKS:



```text

AWS

&#x20;↓

EKS Cluster

&#x20;↓

Node Group

&#x20;↓

Worker Nodes

&#x20;↓

Deployment

&#x20;↓

Pods

&#x20;↓

Service

&#x20;↓

Application

```



\## 🎯 Key Learning



Today I gained practical knowledge of \*\*Kubernetes and Amazon EKS\*\*. I learned how Kubernetes Deployments create Pods, how Services expose applications, and how EKS can be used to run Kubernetes workloads on AWS.



\## 📚 Outcome



By the end of Day 10, I improved my understanding of:



\* Kubernetes

\* Minikube

\* Pods

\* Deployments

\* Services

\* NodePort

\* LoadBalancer

\* Amazon EKS

\* EKS Node Groups

\* AWS VPC and Subnets

\* AWS CLI

\* kubectl

