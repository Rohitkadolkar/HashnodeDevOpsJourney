---
title: "#Day18: Docker Compose for DevOps Engineers #90DaysofDevOps"
datePublished: Mon Apr 10 2023 14:34:48 GMT+0000 (Coordinated Universal Time)
cuid: clgaxqi22000309jz92ql9qpb
slug: day18-docker-compose-for-devops-engineers-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681137249610/596ffb45-0343-4041-add9-590e43e057e3.png
tags: docker, devops, docker-compose

---

## Docker Compose

* Docker Compose is a tool that was developed to help define and share multi-container applications.
    
* With Compose, we can create a YAML file to define the services and with a single command, can spin everything up or tear it all down.
    

## What is YAML?

* YAML is a data serialization language that is often used for writing configuration files. Depending on whom you ask, YAML stands for yet another markup language or YAML ain’t markup language (a recursive acronym), which emphasizes that YAML is for data, not documents.
    
* YAML is a popular programming language because it is human-readable and easy to understand.
    
* YAML files use a .yml or .yaml extension.
    

## Task-1

### Learn how to use the docker-compose.yml file, to set up the environment, configure the services and links between different containers, and also to use environment variables in the docker-compose.yml file.

**To create a docker file, go to the directory in which all app files are saved, and start vim editor**

`vim docker-compose.yaml`

**write the following in vim editor:**

```yaml
version: "3.9"
services:
  web_app:
    container_name: "django-todo-app"
    build: .
    ports:
      - 8000:8000
    volumes:
      - django-todo-volume:/app
  my-db:
    container_name: "django-mysql-db"
    image: mysql:5.7
    ports:
      - 3306:3306
    environment:
      MYSQL_ROOT_PASSWORD: "test@123"
volumes:
  django-todo-volume:
```

**The docker-compose YAML file is basically the build and run command clubbed together and written like a script in YAML format.**

**To run the docker-compose file, use command:**

`docker-compose up`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681132990512/65d389c9-c826-487f-a2c3-dd7a7ce2b46c.png align="center")

**But if you perform** `docker ps`**, your container will not show as running.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681133056100/4bfb45b7-944f-4354-89ce-d8b00ae761f0.png align="center")

**so use:**

`docker-compose up -d`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681133125129/9e893a44-f0c7-4e12-babb-41d7ab4b6697.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681133136641/4196302b-cca8-4bcc-b999-e1a9692e1c53.png align="center")

**It is now visible in running operations.**

**Now copy the public key of the instance and use the following url**

**&lt;publicIP&gt;:&lt;portassigned&gt;**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681133272957/05f60be6-42cb-4bd6-b14c-d4edf3a1fa00.png align="center")

**The app is now accessible!**

## Task-2

### Pull a pre-existing Docker image from a public repository (e.g. Docker Hub) and run it on your local machine. Run the container as a non-root user (Hint- Use `usermod` command to give user permission to docker). Make sure you reboot instance after giving permission to user.

**Search for the image to be pulled from docker hub using**

`docker pull <image>`

**Here we are using mysql**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681133538254/d97e7482-08c1-48da-8b5f-40a60160b6c0.png align="center")

`sudo usermod -a -G docker ubuntu`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681133814752/a3023060-8589-4fd5-b829-d910627c87c0.png align="center")

**sudo reboot**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681134049639/60e18659-442c-4f28-bb5e-cb7de475ab71.png align="center")

### Inspect the container's running processes and exposed ports using the docker inspect command.

**Use docker ps to check all process IDs of running containers**

`docker ps`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681134471367/b546c725-e2c5-4e62-849f-b709daa04163.png align="center")

**docker inspect &lt;containerid&gt;**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681134486127/73bd35f9-a2f2-4d70-aeec-a5e71c2c1bc1.png align="center")

**Use the docker logs command to view the container's log output.**

`docker logs <containerID>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681134584145/fb1a9cb9-b9b2-413a-9551-21e43647f517.png align="center")

**Use the docker stop and docker start commands to stop and start the container.**

`docker stop <containerID>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681134802828/c0aa573e-aa41-4a79-9b1f-163bf61fc9a9.png align="center")

`docker start <containerID>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681134851035/58ef8b90-7984-4e7b-bec4-b58d8f7eacb2.png align="center")

**Use the docker rm command to remove the container when you're done.**

**docker rm &lt;containerid&gt;**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681136688362/9ec5d594-beb4-48d1-9fbc-d4b70ee15d44.png align="center")

## How to run Docker commands without sudo?

**Make sure docker is installed and system is updated (This is already been completed as a part of previous tasks):**

**sudo usermod -a -G docker $USER**

**Reboot the machine.**