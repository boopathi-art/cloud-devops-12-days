# Day 4 – Docker Compose, Networking & Jenkins

## 📅 Day 4 Summary

Today I practiced **Docker Compose, multi-container applications, Docker networking, Java setup, Docker version/update commands, and Jenkins troubleshooting** using PowerShell.

## 📚 Topics Covered

* Docker version and Docker Compose version
* Docker Desktop update using Winget
* Docker container management
* Docker Compose
* Multi-container applications
* Custom Docker networks
* Container-to-container communication
* Docker network mapping
* Docker port mapping
* Docker volumes
* Apache HTTP Server
* PHP with Apache
* MySQL container
* Microsoft OpenJDK 11
* Java version verification
* Jenkins service management
* Jenkins troubleshooting

## 🐳 Docker Version Commands

```powershell
docker --version
docker compose version
docker version
```

## 🔄 Update Docker Desktop

Used Winget to check and update Docker Desktop:

```powershell
winget upgrade --id Docker.DockerDesktop
```

## 🌐 Docker Network

Created a custom Docker network named:

```text
sjc-demonet
```

### Commands

```powershell
docker network create sjc-demonet
# Day 4 – Docker Compose, Networking & Jenkins

## 📅 Day 4 Summary

Today I practiced **Docker Compose, multi-container applications, Docker networking, Java setup, Docker version/update commands, and Jenkins troubleshooting** using PowerShell.

## 📚 Topics Covered

* Docker version and Docker Compose version
* Docker Desktop update using Winget
* Docker container management
* Docker Compose
* Multi-container applications
* Custom Docker networks
* Container-to-container communication
* Docker network mapping
* Docker port mapping
* Docker volumes
* Apache HTTP Server
* PHP with Apache
* MySQL container
* Microsoft OpenJDK 11
* Java version verification
* Jenkins service management
* Jenkins troubleshooting

## 🐳 Docker Version Commands

```powershell
docker --version
docker compose version
docker version
```

## 🔄 Update Docker Desktop

Used Winget to check and update Docker Desktop:

```powershell
winget upgrade --id Docker.DockerDesktop
```

## 🌐 Docker Network

Created a custom Docker network named:

```text
sjc-demonet
```

### Commands

```powershell
docker network create sjc-demonet
docker network ls
docker network inspect sjc-demonet
```

Connected an existing container:

```powershell
docker network connect sjc-demonet <container-name>
```

Run a container directly on the custom network:

```powershell
docker run -d --network sjc-demonet -p 8080:80 nginx
```

## 🔗 Docker Network Mapping

### Objective

Created and configured a custom Docker network to enable communication between multiple containers.

### Tasks Performed

* Created a custom Docker network using `docker network create`.
* Verified the network using `docker network ls`.
* Connected containers to `sjc-demonet`.
* Inspected network configuration using `docker network inspect`.
* Connected existing containers using `docker network connect`.
* Practiced Docker port mapping using `-p`.
* Verified running containers using `docker ps`.

### Key Learning

Docker custom networks allow containers to communicate with each other using container names or service names.

For example:

```text
Container A
     ↓
sjc-demonet
     ↓
Container B
```

Port mapping connects a container service to the host machine:

```text
Host Port → Container Port
8080      → 80
```

## 🐳 Docker Compose

Practiced creating and managing a multi-container application using Docker Compose.

### Services

#### Frontend

* Apache HTTP Server
* Image: `httpd:2.4`
* Port: `8082:80`

#### Backend

* PHP with Apache
* Image: `php:8.2-apache`
* Port: `8081:80`

#### Database

* MySQL
* Image: `mysql:8.0`
* Database: `myapp`
* User: `appuser`

## 🔧 Docker Compose Commands

Pull the required images:

```powershell
docker compose pull
```

Start services in detached mode:

```powershell
docker compose up -d
```
Check running Compose services:

```powershell

docker compose ps
```


## 🌐 Application Network

The application used a Docker network:


```text
app-network
```

Connected services:

```text
frontend
backend
database

```


The backend can communicate with MySQL using:

```text
database:3306
```

Instead of:

```text
localhost:3306
```

This is because containers communicate through the Docker network using service/container names.


## 💾 Docker Volume

Created a persistent MySQL volume:

```text
mysql-data
```

The volume allows MySQL data to remain available when the database container is recreated.

```text
MySQL Container
      ↓
 mysql-data
      ↓
Persistent Database Storage
```

## 🔌 Port Mapping

| Service  | Host Port | Container Port |
| -------- | --------: | -------------: |
| Jenkins  |      8080 |           8080 |
| Frontend |      8082 |             80 |
| Backend  |      8081 |             80 |
| MySQL    |  Internal |           3306 |

## ☕ Java Setup

Installed and configured **Microsoft OpenJDK 11**.

Verified Java installation:

```powershell
java -version
javac -version
```

Java version used:

```text
OpenJDK 11.0.32.1 LTS
```

Also practiced upgrading the Java environment to **Java 25**.

## 🔧 Jenkins Troubleshooting

Worked with Jenkins running on:

```text
Port: 8080
```

Jenkins service commands:

```powershell
Get-Service jenkins
Start-Service jenkins
```

Checked port 8080:

```powershell
netstat -ano | findstr :8080
```

Checked Jenkins service:

```powershell
sc.exe query jenkins
```

Checked Jenkins service configuration:

```powershell
sc.exe qc jenkins
```

Investigated the following connection problem:

```text
ERR_CONNECTION_REFUSED
```

while accessing:

```text
http://localhost:8080/
```

## 🧪 Docker Verification

Checked running containers:

```powershell
docker ps
```

Checked all containers:

```powershell
docker ps -a
```

Verified Docker network:

```powershell
docker network ls
```

Inspected network details:

```powershell
docker network inspect sjc-demonet
```

## 📚 Key Concepts Learned

* Docker Compose
* Multi-container applications
* Docker custom networks
* Container-to-container communication
* Docker network mapping
* Port mapping
* Docker volumes
* Apache HTTP Server
* PHP-Apache
* MySQL containers
* Docker Compose services
* Java/OpenJDK installation
* Jenkins service management
* Jenkins port troubleshooting
* Docker Desktop updates

## 🎯 Day 4 Outcome

Successfully practiced **Docker Compose, multi-container applications, Docker networking, persistent storage, Java setup, and Jenkins troubleshooting**.

The main workflow practiced was:

```text
Docker
   ↓
Docker Network
   ↓

Multiple Containers

   ↓
Docker Compose

   ↓

Frontend + Backend + Database

   ↓
Persistent Volume

   ↓

Java Setup
   ↓
Jenkins
   ↓
Troubleshooting
```


## 📸 Day 4 Screenshot


#Docker #DockerCompose #DockerNetworking #Jenkins #Java #DevOps #CloudComputing #Containerization #GitHub #LearningDevOps
The Day 4 command screenshot documents the commands and practical work performed during the session.

## ✅ Day 4 Completed

**Docker → Docker Network → Container Mapping → Docker Compose → Multi-Container Application → Volume → Java → Jenkins**
