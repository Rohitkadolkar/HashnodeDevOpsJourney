---
title: "#Day19 : Docker for DevOps Engineers #90DaysofDevOps"
datePublished: Tue Apr 18 2023 19:30:16 GMT+0000 (Coordinated Universal Time)
cuid: clgmntaas000e09ju2vjfeafl
slug: day19-docker-for-devops-engineers-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681846185048/4857a040-01d7-4275-a2a6-19bbd2390ee2.jpeg
tags: docker, devops

---

# Docker-Volume

Docker allows you to create something called volumes. Volumes are like separate storage areas that can be accessed by containers. They allow you to store data, like a database, outside the container, so it doesn't get deleted when the container is deleted. You can also mount from the same volume and create more containers having same data.

![Volumes on the Docker host](https://docs.docker.com/storage/images/types-of-mounts-volume.png align="left")

# Docker Network

Docker allows you to create virtual spaces called networks, where you can connect multiple containers (small packages that hold all the necessary files for a specific application to run) together. This way, the containers can communicate with each other and with the host machine (the computer on which the Docker is installed). When we run a container, it has its own storage space that is only accessible by that specific container. If we want to share that storage space with other containers, we can't do that.

## Task-1

Create a multi-container docker-compose file which will bring *UP* and bring *DOWN* containers in a single shot ( Example - Create application and database container )

Use the `docker-compose up` command with the `-d` flag to start a multi-container application in detached mode.

**For this lets clone the code of an app from Github first**

**For that, copy the link of repo from GitHub:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681644999905/64236eda-4721-424b-988a-81c24033e96b.png align="center")

**In our Linux machine, use command**

`git clone <repo link>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681645085860/5209b0ac-3c8e-4359-9c30-f5a0eddee926.png align="center")

**The repo is now cloned on local machine**

`cd django-todo-cicd`

**Since, we are creating a docker-compose file from scratch, deleting the docker-compose.yml file.**

**Now lets create a docker-compose.yaml file from scratch**

`vim docker-compose.yaml`

**Now write the following code:**

```yaml
version : "3.3"
services :
  my_web_app:
    container_name: "django-todo-app"
    build: .
    ports:
      - 8000:8000
    volumes:
      - django-todo-volume:/app
  my_db:
    container_name: "django-mysql-db"
    image: mysql:5.7
    ports:
      - 3306:3306
    environment:
      MYSQL_ROOT_PASSWORD: "test@123"
volumes:
  django-todo-volume:
```

**Now use command:**

`docker-compose up -d`

**Use the** `docker-compose ps` **command to view the status of all containers, and** `docker-compose logs` **to view the logs of a specific service.**

**Now check whether container is running using** `docker-compose ps`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681824169118/be972250-f2c9-42db-a9a1-1778b238bedc.png align="center")

**Thus multiple containers are now created using a single docker compose file**

**Use** `docker-compose` **logs to check the logs**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681824605974/768eb8c8-1aa6-490e-b4b8-153f4dca30e7.png align="center")

**Use the** `docker-compose down` **command to stop and remove all containers, networks, and volumes associated with the application**

**Now, to stop the containers, use command**

`docker-compose down`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681824679664/e5ad3f1e-2415-4322-a2ef-1a5aaec42ac7.png align="center")

**To check whether they are stopped use command**

`docker ps`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681824831908/debad3cc-d14c-40b6-8518-cf468f822b92.png align="center")

**The containers are now stopped.**

### Task-2

Learn how to use Docker Volumes and Named Volumes to share files and directories between multiple containers.

**Create a diectory for volumes using**

`mkdir volumes`

**Now create a docker volume using**

`sudo docker volume create my_volume`

**Inspect the volume using**

`docker volume inspect my_volume`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681843667721/29526629-412d-455b-bd48-aecec4534024.png align="center")

Create two or more containers that read and write data to the same volume using the `docker run --mount` command.

`sudo docker run -d -p 8000:8000 --mount source=my_volume,target=/app django-todo-app:latest`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681844076984/902ae464-c8ea-46f3-9943-bd9afe1ec54c.png align="center")

`sudo docker run -d -p 8001:8001 --mount source=my_volume,target=/app django-todo-cicd_my_web_app:latest`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681844567149/eb0283a3-510a-457f-b44c-cd9435815fca.png align="center")

Verify that the data is the same in all containers by using the docker exec command to run commands inside each container.

`docker exec -it <cont id> sh`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681845149697/9f20e7d9-b0d4-43ce-a480-3cf145b79fc4.png align="center")

Use the docker volume ls command to list all volumes and docker volume rm command to remove the volume when you're done.

`docker volume ls`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681845218944/f68b71bb-44ab-4d2b-9ee2-5e883744a1f3.png align="center")

**To remove volume**

`docker volume rm my_volume`

**If it returns error saying volume in use, enter command:**

`docker container prune`

**Now try to remove volume**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681845747999/0b2335ad-907d-4caa-8f6a-b5cf1f81ec82.png align="center")