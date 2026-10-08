\# Day 9 – Kubernetes \& Minikube Practice



\## 📌 Overview



Today I practiced the fundamentals of \*\*Kubernetes using Minikube with Docker\*\*. I learned how to create and manage Pods and Deployments, scale applications, check Kubernetes resources, view container logs, access containers, and delete Kubernetes resources.



\## 🛠️ Tools Used



\* Kubernetes

\* Minikube

\* Docker

\* kubectl

\* Nginx

\* Python

\* Apache HTTP Server



\## 📚 Topics Practiced



\### 1. Minikube Cluster



Started and verified a Kubernetes cluster using the Docker driver.



```bash

minikube start --driver=docker

```



Checked Minikube status:



```bash

minikube status

```



Checked Kubernetes nodes:



```bash

minikube kubectl -- get nodes

```



Checked all Pods:



```bash

minikube kubectl -- get pods -A

```



\---



\### 2. Creating a Pod



Created an Apache Pod using the `httpd` image:



```bash

minikube kubectl -- run apachepod --image=httpd

```



Checked the Pod:



```bash

minikube kubectl -- get pods

```



Viewed Pod logs:



```bash

minikube kubectl -- logs apachepod

```



Accessed the Apache container:



```bash

minikube kubectl -- exec -it apachepod -- /bin/sh

```



Deleted the Pod:



```bash

minikube kubectl -- delete pod apachepod

```



\---



\### 3. Creating a Deployment



Created a Deployment using the Python image:



```bash

minikube kubectl -- create deployment demodeploy --image=python

```



Checked the Deployment:



```bash

minikube kubectl -- get deploy

```



Deleted the Deployment:



```bash

minikube kubectl -- delete deployment demodeploy

```



\---



\### 4. Creating an Nginx Deployment



Created an Nginx Deployment using the `nginx:1.30` image:



```bash

minikube kubectl -- create deployment nginxdeploy --image=nginx:1.30

```



Checked the Deployment:



```bash

minikube kubectl -- get deploy

```



Initial result:



```text

NAME          READY   UP-TO-DATE   AVAILABLE

nginxdeploy   1/1     1            1

```



This confirmed that one Nginx Pod was running and available.



\---



\### 5. Scaling the Deployment



Scaled the Nginx Deployment from \*\*1 replica to 5 replicas\*\*:



```bash

minikube kubectl -- scale deployment nginxdeploy --replicas=5

```



Checked the Deployment:



```bash

minikube kubectl -- get deploy

```



Result:



```text

NAME          READY   UP-TO-DATE   AVAILABLE

nginxdeploy   5/5     5            5

```



This confirmed that Kubernetes successfully created five replicas.



Checked the Pods:



```bash

minikube kubectl -- get pods

```



\---



\### 6. Describing Kubernetes Resources



Used the `describe` command to view detailed information about Kubernetes resources.



For a Deployment:



```bash

minikube kubectl -- describe deployment nginxdeploy

```



For a Pod:



```bash

minikube kubectl -- describe pod <pod-name>

```



\---



\### 7. Deleting the Deployment



Deleted the Nginx Deployment:



```bash

minikube kubectl -- delete deployment nginxdeploy

```



Verified the resources:



```bash

minikube kubectl -- get deployments

```



```bash

minikube kubectl -- get pods

```



\---



\## 💡 Key Learnings



\* \*\*Minikube\*\* provides a local Kubernetes environment for learning and testing.

\* A \*\*Pod\*\* is the smallest deployable unit in Kubernetes.

\* A \*\*Deployment\*\* manages Pods and maintains the desired number of replicas.

\* The `--image` option specifies the container image.

\* \*\*Replicas\*\* define how many copies of a Pod should run.

\* Kubernetes automatically creates or removes Pods when the replica count changes.

\* `kubectl get` is used to view Kubernetes resources.

\* `kubectl describe` provides detailed information about resources.

\* `kubectl logs` displays container logs.

\* `kubectl exec` allows commands to be executed inside a running container.

\* Deleting a Deployment also removes the Pods managed by that Deployment.



\## 🎯 Day 9 Summary



Today I practiced \*\*Kubernetes and Minikube fundamentals\*\*. I created and deleted Pods, created Deployments using Python and Nginx images, viewed logs, accessed containers, described resources, and scaled an Nginx Deployment from \*\*1 replica to 5 replicas\*\*.



\### Main Kubernetes Concept



```text

Deployment

&#x20;    ↓

ReplicaSet

&#x20;    ↓

Multiple Pods

&#x20;    ↓

Containers

```



\### Commands Practiced



```bash

minikube start --driver=docker

minikube status

minikube kubectl -- get nodes

minikube kubectl -- get pods

minikube kubectl -- run apachepod --image=httpd

minikube kubectl -- logs apachepod

minikube kubectl -- create deployment demodeploy --image=python

minikube kubectl -- create deployment nginxdeploy --image=nginx:1.30

minikube kubectl -- scale deployment nginxdeploy --replicas=5

minikube kubectl -- describe deployment nginxdeploy

minikube kubectl -- delete deployment nginxdeploy

```

