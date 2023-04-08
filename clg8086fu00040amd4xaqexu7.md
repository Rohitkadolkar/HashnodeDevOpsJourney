---
title: "#Day17 : Docker Project for DevOps Engineers."
datePublished: Sat Apr 08 2023 13:21:14 GMT+0000 (Coordinated Universal Time)
cuid: clg8086fu00040amd4xaqexu7
slug: day17-docker-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680960032654/b12ef1a1-41a4-406b-a363-5f0e3b148094.png
tags: docker, devops, dockerhub

---

Docker is a tool that makes it easy to run applications in containers. Containers are like small packages that hold everything an application needs to run. To create these containers, developers use something called a Dockerfile.

A Dockerfile is like a set of instructions for making a container. It tells Docker what base image to use, what commands to run, and what files to include. For example, if you were making a container for a website, the Dockerfile might tell Docker to use an official web server image, copy the files for your website into the container, and start the web server when the container starts.

### Tasks

**Create a Dockerfile for a simple web application (e.g. a Node.js or Python app)**

**Step1:**

**Clone a repository having a simple app from github. Go inside the projects folder and use command:**

`git clone <URL>`

**you will find the repository in your projects folder:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680948735639/861dffcc-d9df-47ba-ad5a-382c9c8a6cfd.png align="center")

**go inside the folder using**

`cd <folder name>`

**Check the main file which has to be run is in which format (eg : python, nodejs)**

**Now create a file named Dockerfile**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680949609062/21bc9c36-6a36-477b-a290-b1b16393154c.png align="left")

**Open the file in vim and type the following:**

`FROM python:3.9`

`COPY . .`

`RUN pip install -r requirements.txt`

`CMD ["python","manage.py","runserver","0.0.0.0:8000"]`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680949866107/9afb61ea-31f0-4f70-9e9e-86d669b710b3.png align="center")

**The requirements.txt file contains the required dependencies for the file to run**

**Your Docker file is ready to build an image.**

### Build the image using the Dockerfile and run the container

**To create an image from it, run the following command:**

`docker build -t <image_name:latest> .`

**To run a container from the built image:**

`docker run -d -p 8000:8000 <imagename>`

### Verify that the application is working as expected by accessing it in a web browser

**To access it in a web browser, we need to first enable the port specified in the security group attached to the instance.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680954799795/732767bd-fe65-4f1e-8c3d-79282b65952c.png align="center")

**Now copy the public IP add:&lt;port number&gt;**

**and paste it in browser.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680955911200/c01fa4ab-ca4e-4d15-812b-e740bb47412a.png align="center")

**Congratulations your docker container is up and running !**

### Push the image to a public or private repository (e.g. Docker Hub )

**To tag repository first, use command:**

`docker tag <image_name:tag> <repo_name:tag>`

**Log in to docker**

`docker login`

**Enter credentials used for the docker hub account**

**now you can push using the following code:**

`docker push <repo_name:tag>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680959791527/8269f75a-2e99-4b81-ac68-e515a512e127.png align="center")

**Your image is now pushed onto docker hub:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680959842215/13f9b5ff-9bfc-4a6b-9d90-e14890bbc4d8.png align="center")