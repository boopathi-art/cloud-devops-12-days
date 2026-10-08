\# Day 8 – Kubernetes Fundamentals



\## 📅 Date



6 October 2026



\## 📌 Overview



Today I learned the basic architecture of \*\*Kubernetes\*\* and understood the responsibilities of the \*\*Control Plane\*\* and \*\*Worker Nodes\*\*.



\## 📚 Topics Covered



\### 1. Kubernetes



Kubernetes is a container orchestration platform used to deploy, manage, scale, and maintain containerized applications.



\### 2. Control Plane Components



The \*\*Control Plane\*\* acts as the brain of the Kubernetes cluster.



\#### API Server



\* Main communication point of the Kubernetes cluster.

\* Receives requests from `kubectl` and other Kubernetes components.

\* Provides the Kubernetes API.



\#### Scheduler



\* Decides which Worker Node should run a newly created Pod.

\* Considers available resources and scheduling requirements.



\#### Controller Manager



\* Continuously monitors the cluster.

\* Ensures the actual state matches the desired state.

\* Manages different Kubernetes controllers.



\### 3. Kubernetes Controllers



Controllers continuously monitor Kubernetes resources and take action to maintain the desired state.



Important controllers learned:



\* Deployment Controller

\* ReplicaSet Controller

\* Node Controller

\* Job Controller

\* CronJob Controller

\* StatefulSet Controller

\* DaemonSet Controller

\* Namespace Controller



\### 4. Worker Node Components



Worker Nodes are the machines where Pods and application containers run.



\#### Kubelet



\* Runs on every Worker Node.

\* Communicates with the API Server.

\* Ensures assigned Pods are running correctly.



\#### Container Runtime



\* Responsible for running containers.

\* Examples:



&#x20; \* `containerd`

&#x20; \* `CRI-O`



\#### kube-proxy



\* Handles Kubernetes Service networking.

\* Helps route network traffic to the appropriate Pods.



\---



\## 🏗️ Kubernetes Architecture



```text

&#x20;                   Kubernetes Cluster

&#x20;                          |

&#x20;            +-------------+-------------+

&#x20;            |                           |

&#x20;      Control Plane                 Worker Node

&#x20;            |                           |

&#x20;    +-------+--------+          +-------+-------+

&#x20;    |       |        |          |       |       |

&#x20;API Server Scheduler Controller Kubelet Runtime kube-proxy

&#x20;                   Manager              |

&#x20;                                         |

&#x20;                                        Pods

&#x20;                                         |

&#x20;                                     Containers

```



\---



\## 📸 Screenshot



\### Kubernetes Architecture



!\[Kubernetes Architecture](Kubernetes%20Architecture.png)



\---



\## 💡 Key Learning



\* Kubernetes manages containerized applications.

\* The \*\*Control Plane\*\* manages the cluster.

\* The \*\*API Server\*\* handles Kubernetes requests.

\* The \*\*Scheduler\*\* selects a suitable Worker Node for Pods.

\* The \*\*Controller Manager\*\* maintains the desired state.

\* \*\*Kubelet\*\* manages Pods on Worker Nodes.

\* \*\*Container Runtime\*\* runs containers.

\* \*\*kube-proxy\*\* handles Service networking.



\---



\## 💻 Basic Kubernetes Commands



```bash

kubectl get nodes

kubectl get pods

kubectl get deployments

kubectl get services

```



\### `kubectl get nodes`



Displays the nodes available in the Kubernetes cluster.



\### `kubectl get pods`



Displays Pods running in the current namespace.



\### `kubectl get deployments`



Displays Kubernetes Deployments.



\### `kubectl get services`



Displays Kubernetes Services.



\---



\## 🔄 Kubernetes Workflow



```text

&#x20;                User

&#x20;                 |

&#x20;               kubectl

&#x20;                 |

&#x20;            API Server

&#x20;                 |

&#x20;       +---------+---------+

&#x20;       |                   |

&#x20;   Scheduler        Controller Manager

&#x20;       |                   |

&#x20;       +---------+---------+

&#x20;                 |

&#x20;            Worker Node

&#x20;                 |

&#x20;              Kubelet

&#x20;                 |

&#x20;         Container Runtime

&#x20;                 |

&#x20;                Pod

&#x20;                 |

&#x20;             Container

```



\---



\## 📖 Summary



Today I gained a basic understanding of \*\*Kubernetes architecture, Control Plane components, Controllers, and Worker Node components\*\*.



I learned how Kubernetes coordinates \*\*Pods, containers, scheduling, networking, and desired-state management\*\*.





