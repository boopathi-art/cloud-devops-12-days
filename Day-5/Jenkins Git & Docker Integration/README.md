\# Day 5 – Jenkins Git \& Docker Integration

\## 🎯 Objective



Configured a basic CI/CD workflow integrating \*\*GitHub, Jenkins, and Docker\*\*. Jenkins fetches the source code from GitHub, builds a Docker image using a Dockerfile, and runs the Docker container.



\## 🛠️ Technologies Used



\* Git \& GitHub

\* Jenkins

\* Docker

\* Nginx

\* PowerShell

\* Windows 11



\## 🔧 Tasks Completed



\### 1. GitHub Repository Setup



\* Created the `jenkins` GitHub repository.

\* Initialized the local Git repository.

\* Created the `main` branch.

\* Added project files.

\* Committed and pushed files to GitHub.

\* Configured Jenkins GitHub authentication.



\### 2. Jenkins Job Creation



Created the Jenkins Freestyle project:



```text

demo-integration-git-docker-sjce

```



Configured:



\* GitHub repository URL

\* Git credentials: `boopathi-git`

\* `main` branch

\* Jenkins workspace

\* Windows batch build steps



\### 3. Git Integration



Jenkins successfully:



\* Connected to GitHub.

\* Fetched the remote repository.

\* Checked out the `main` branch.

\* Retrieved the latest commit.

\* Copied project files into the Jenkins workspace.



\### 4. Dockerfile



Created a Dockerfile using Nginx:



```dockerfile

FROM nginx:alpine

COPY README.md /usr/share/nginx/html/index.html

EXPOSE 80

```



\### 5. Docker Image Build



Jenkins used the following command:



```bat

docker build -t jenkins:latest .

```



This creates the Docker image:



```text

jenkins:latest

```



\### 6. Check Docker Images



```bat

docker image ls

```



\### 7. Docker Container Deployment



To remove an existing container:



```bat

docker rm -f jenkinstestcon 2>NUL

```



To run the Docker container:



```bat

docker run -d --name jenkinstestcon -p 8084:80 jenkins:latest

```



\### 8. Verify Running Container



```bat

docker ps

```



The container used:



```text

Container Name : jenkinstestcon

Image          : jenkins:latest

Host Port      : 8084

Container Port : 80

```



\## 🌐 Application Access



After the Jenkins build completes successfully:



```text

http://localhost:8084

```



The Nginx application is exposed through host port `8084`.



\## 🔄 Complete CI/CD Workflow



```text

GitHub

&#x20;  ↓

Jenkins

&#x20;  ↓

Git Checkout

&#x20;  ↓

Docker Build

&#x20;  ↓

jenkins:latest

&#x20;  ↓

Docker Run

&#x20;  ↓

jenkinstestcon

&#x20;  ↓

localhost:8084

```



\## 📌 Git Commands Practiced



```bash

git init

git branch -M main

git add .

git commit -m "Initial Jenkins integration project"

git push -u origin main

git pull origin main

```



\## 🐳 Docker Commands Practiced



```bat

docker build -t jenkins:latest .

docker image ls

docker rm -f jenkinstestcon 2>NUL

docker run -d --name jenkinstestcon -p 8084:80 jenkins:latest

docker ps

```



\## 📸 Screenshots



\### Jenkins Build / Docker Integration



!\[Jenkins Build](Screenshot%202026-09-30%20165156.png)



\### Jenkins Build Result



!\[Jenkins Result](Screenshot%202026-09-30%20165105.png)



\### Git Push and Pull Commands



!\[Git Push Pull](jenkins%20push%20and%20pull%20command%20.png)



\## 📚 Key Learning



\* GitHub repository integration with Jenkins

\* Jenkins Freestyle project configuration

\* Jenkins Git credentials

\* Git branch configuration

\* Jenkins workspace

\* Dockerfile creation

\* Docker image building

\* Docker container execution

\* Nginx container deployment

\* Port mapping

\* Basic CI/CD workflow





