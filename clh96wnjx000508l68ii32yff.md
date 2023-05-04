---
title: "#Day24 : Day 24 Task: Complete Jenkins CI/CD Project"
datePublished: Thu May 04 2023 13:55:42 GMT+0000 (Coordinated Universal Time)
cuid: clh96wnjx000508l68ii32yff
slug: day24-day-24-task-complete-jenkins-cicd-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683208485697/646c8a87-b1f2-4004-a332-5fdbdcc1d6d0.jpeg
tags: devops, jenkins, ci-cd

---

Let's make a beautiful CI/CD Pipeline for your Node JS Application 😍

Day 23 was all about Jenkins CI/CD, make sure you have done it and understanding the concepts.

As we have worked with Docker and Docker compose, it will be good if we use it in a live project.

# Task-01

* **Fork node-todo-cicd repository:**
    
* **Create a connection to your Jenkins job and your GitHub Repository via GitHub Integration.**
    
* **Read About** [**GitHub WebHooks**](https://betterprogramming.pub/how-too-add-github-webhook-to-a-jenkins-pipeline-62b0be84e006) **and make sure you have CICD setup**
    

Go to the [https://github.com/LondheShubham153/node-todo-cicd.git](https://github.com/LondheShubham153/node-todo-cicd.git) and fork the repository.

In the previous blog, we have already created a freestyle project called first-Jenkins-project. Let's make some modifications to the same.

Select Github project and provide link for the github project.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683196687720/417ff2a8-3082-4453-af74-d57caa86c3e7.png align="center")

In source-code management, select Git and give URL and give credentials ubuntu (dev-key)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683196827162/63a1737b-97c2-45e2-bc6c-c407442dc67c.png align="center")

and specify branch

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683196883909/98481d6a-3947-4c82-aa41-e5499afef6f1.png align="center")

In build triggers, select "GitHub hook trigger for GITScm polling"[  
](http://54.157.236.240:8080/job/First%20jenkins%20project/configure#)

**What is a Github webhook?**

Webhooks allow you to build or set up integrations, such as GitHub Apps or OAuth Apps, which subscribe to certain events on GitHub.com. When one of those events is triggered, a HTTP POST payload will be sent to the webhook's configured URL.

When changes are made in any file in Github, a it will automatically trigger a build in the jenkins, hence providing continuous deployment.

# Task-02

* In the Execute shell run the application using Docker compose
    
* You will have to make a Docker Compose file for this Project (Can be a good open source contribution)
    
* Run the project and give yourself a treat:)
    

Previously, we used docker build and docker run commands as separate commands.

However in this hands-on, we will create a docker-compose file and run it via jenkins.

To create a docker-compose file, first of all git clone the app files on your agent server from github using

`git clone <github url>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683198002127/0eb6f197-6f64-4944-bd15-3a932e158e97.png align="center")

You will get the file in your directory.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683198082372/55059b4c-2321-4a38-83f6-1646d9757bb5.png align="center")

Go inside the node-todo-cicd using `cd node-todo-cicd` and delete the docker file as we will be building it again from scratch.

So delete the existing docker-file first.

Create a docker-file.yaml file and type the following YAML script inside it -

```yaml
version : '3.9'

services:
  web:
   image: trainwithshubham/node-todo-app-cicd:latest
   ports:
     - "8000:8000"
```

Now go to the jenkins execute shell command and type the following

`cd /home/ubuntu/projects/node-todo-cicd`

`docker compose down`

`docker compose up -d`

Save the project and click on build now

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683207972506/d207b7d3-6277-420d-bb3b-1b6f167f6abf.png align="center")

Paste the private ip of the agent server with port 8000 and check whether it is working -

[http://44.203.156.50:8000](http://44.203.156.50:8000/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683208126247/2ec4ea0a-0f52-4488-81e0-256ce9411e86.png align="center")

The website will be up and running.

You can see the console output as well.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683208227485/51766480-d6aa-4f87-a81b-ea827a609b51.png align="center")