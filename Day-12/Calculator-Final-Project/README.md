\# Day 12 – Calculator Final Project



\## Overview



A web-based calculator developed using HTML, CSS, and JavaScript. This project demonstrates frontend development, Docker containerization, and DevOps practices.



\## Technologies Used



\* HTML

\* CSS

\* JavaScript

\* Git and GitHub

\* Docker

\* Jenkins

\* GitHub Container Registry (GHCR)

\* Terraform (if used in this project)



\## Project Structure



\* `index.html` – Calculator interface

\* `style.css` – Styling and layout

\* `script.js` – Calculator functionality

\* `Dockerfile` – Docker image build instructions

\* `terraform/` – Infrastructure configuration files, if applicable



\## Run with Docker



Build the image:



```bash

docker build -t calculator:latest .

```



Run the container:



```bash

docker run -d --name calculator-container -p 8085:80 calculator:latest

```



Open the application at:



http://localhost:8085



Remove the container after testing:



```bash

docker rm -f calculator-container

```



\## Learning Outcomes



\* Developed an interactive web application.

\* Practiced source-code management with Git and GitHub.

\* Packaged the application using Docker.

\* Explored CI/CD automation using Jenkins.

\* Practiced container image publishing with GHCR.



\## Project Repository



https://github.com/boopathi-art/calculator



\## Author



Cloud Computing Student | DevOps Final Project

