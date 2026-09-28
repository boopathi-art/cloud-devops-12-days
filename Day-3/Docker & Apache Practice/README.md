# Day 3 – Docker & Apache Practice

## 📅 Day 3

Today I practiced Docker fundamentals by creating and running an Apache HTTP server container and hosting a static HTML website.

## 📚 Topics Covered

* Docker Images
* Docker Containers
* Apache HTTP Server
* Docker Hub Images
* Container Port Mapping
* Docker Volumes
* `docker exec`
* `docker commit`
* Dockerfile
* `docker build`
* `docker run`
* `docker start`
* `docker stop`
* `docker rm`
* `docker ps`
* `docker images`
* `docker history`

## 🐳 Docker Commands Practiced

### 1. Check Docker Version

```bash
docker --version
```

### 2. Download Apache Image

```bash
docker pull httpd:latest
```

### 3. Run Apache Container

```bash
docker run -d --name task -p 8080:80 httpd:latest
```

* `-d` → Runs the container in detached mode.
* `--name task` → Gives the container the name `task`.
* `-p 8080:80` → Maps host port `8080` to container port `80`.
* `httpd:latest` → Uses the latest Apache HTTP Server image.

### 4. Check Running Containers

```bash
docker ps
```

### 5. Check All Containers

```bash
docker ps -a
```

### 6. Check Docker Images

```bash
docker images
```

### 7. Enter the Apache Container

```bash
docker exec -it task bash
```

### 8. Check Apache Website Files

Inside the container:

```bash
ls /usr/local/apache2/htdocs
```

The default Apache website files are stored in:

```text
/usr/local/apache2/htdocs
```

### 9. Exit the Container

```bash
exit
```

## 📦 Docker Commit

Created a new Docker image from the existing container:

```bash
docker commit task snaping:1.0
```

Check the image:

```bash
docker images
```

## 🚀 Run the Committed Image

```bash
docker run -d --name task1 -p 81:80 snaping:1.0
```

Check:

```bash
docker ps
```

The website can be accessed using:

```text
http://localhost:81
```

## 🌐 Static Website Using Apache

Created an `index.html` file and hosted it using Apache inside Docker.

Example:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Docker Website</title>
</head>
<body>
    <h1>Hello from Docker Apache!</h1>
    <p>This website is running inside an Apache Docker container.</p>
</body>
</html>
```

## 📝 Dockerfile

Created a custom Docker image using a Dockerfile:

```dockerfile
FROM httpd:latest

COPY index.html /usr/local/apache2/htdocs/index.html
```

### Dockerfile Explanation

```dockerfile
FROM httpd:latest
```

Uses the official Apache HTTP Server image as the base image.

```dockerfile
COPY index.html /usr/local/apache2/htdocs/index.html
```

Copies the local `index.html` file into the Apache website directory inside the container.

## 🔨 Build Custom Docker Image

```bash
docker build -t customing:latest .
```

Check the image:

```bash
docker images
```

## 🚀 Run Custom Image

```bash
docker run -d --name custom-task -p 83:80 customing:latest
```

### Port Mapping

```text
Host Port       Container Port
    83     →         80
```

Open the website:

```text
http://localhost:83
```

## 🔍 Check Docker Image History

```bash
docker history customing:latest
```

Other images tested:

```bash
docker history httpd:latest
```

```bash
docker history snaping:1.0
```

`docker history` shows the layers and commands used to create a Docker image.

## 🛑 Stop Containers

```bash
docker stop task
```

```bash
docker stop task1
```

```bash
docker stop custom-task
```

## ▶️ Start a Stopped Container

```bash
docker start task
```

## 🗑️ Remove a Container

First stop the container if it is running:

```bash
docker stop task
```

Then remove it:

```bash
docker rm task
```

## 📋 Containers Created

| Container     | Image              | Port      |
| ------------- | ------------------ | --------- |
| `task`        | `httpd:latest`     | `8080:80` |
| `task1`       | `snaping:1.0`      | `81:80`   |
| `custom-task` | `customing:latest` | `83:80`   |

## 🔄 Docker Workflow

```text
Docker Hub
    ↓
httpd:latest
    ↓
docker run
    ↓
Apache Container
    ↓
docker exec
    ↓
Apache Website Files
    ↓
docker commit
    ↓
Custom Docker Image
    ↓
Dockerfile
    ↓
docker build
    ↓
customing:latest
    ↓
docker run
    ↓
Static Website
    ↓
http://localhost:83
```

## 🎯 What I Learned

* Difference between a Docker image and a container.
* How to pull an Apache image from Docker Hub.
* How to run an Apache web server inside Docker.
* How to map host ports to container ports.
* How to check running and stopped containers.
* How to access a running container using `docker exec`.
* How to locate Apache website files inside a container.
* How to create a Docker image using `docker commit`.
* How to create a custom Docker image using a Dockerfile.
* How the `FROM` instruction defines a base image.
* How the `COPY` instruction copies website files into the container.
* How to build a custom image using `docker build`.
* How to run a custom Docker image.
* How to host a static website using Apache and Docker.
* How to inspect Docker image layers using `docker history`.
* How to start, stop, and remove Docker containers.

## 📸 Day 3 Screenshots

The following screenshots document my Day 3 Docker and Apache practice:

1. `day3.png`
2. `day3 (2).png`
3. `day3 (3).png`

## 🌐 Website

The custom Apache website was accessed locally using:

```text
http://localhost:83
```

## ✅ Day 3 Completed

**Docker → Apache → Container → Dockerfile → Custom Image → Static Website → Image History**

### Hashtags

#Docker #Apache #Dockerfile #DevOps #CloudComputing #Containerization #GitHub #LearningDevOps

