---
title: "#Day17 part-2 Docker Project for DevOps Engineers. #90DaysofDevOps"
datePublished: Sun Apr 09 2023 17:27:28 GMT+0000 (Coordinated Universal Time)
cuid: clg9ogouv000309jwf5qo9c8u
slug: day17-part-2-docker-project-for-devops-engineers-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681061205179/11c84525-8e4d-474b-8412-8d22d3ba954f.png
tags: docker, nginx, devops

---

### Route a Django code through Nginx

**Create a Docker file for an app** [**django-notes-app**](https://github.com/LondheShubham153/django-notes-app) **from scratch.**

**Build an image using the Docker file and run a container.**

**Verify that the application is working as expected by accessing it in a web browser.**

**Push the image to a public or private repository (e.g. Docker Hub )**

**Install Nginx on your linux machine**

**Update your linux system using** `sudo apt update` **first in order to install Nginx.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681003848403/f2068f8c-cbc2-4bbc-b181-5014e06e0380.png align="center")

**Once update is complete, install nginx using**

`sudo apt install nginx`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681003957222/46239b53-3f27-4743-bd7f-cfa017dd04d2.png align="center")

**To check whether nginx in active, use**

`systemctl status nginx`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681004026222/749bda29-af7b-4103-b4a4-11a1eeb0f31a.png align="center")

**Create a folder called projects and clone the code from github using following command:**

`git clone <github_repo_link>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681006378935/411feb49-d930-4e54-8f7b-587ca1aa9913.png align="left")

**go inside the folder using**

`cd django-notes-app`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681006484480/0fb3f37b-a9fe-4ed9-8642-78b2b0b2f56b.png align="center")

**To learn how to install docker, refer to my previous blog.**

**now lets build a docker file from scratch:**

**Create and open a file using the vim editor:**

`vim Dockerfile`

**Enter the following code in vim editor:**

```python
FROM python:3.9
COPY . .
RUN pip install -r requirements.txt
CMD ["python","manage.py","runserver","0.0.0.0:<portassign>"]
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681007434017/f84b9c94-a4b4-4a34-9b07-874f63dfb905.png align="center")

**Now that the docker file is ready, let's build an image from the docker file:**

`docker build -t django-notes-app:latest .`

**check using** `docker ps` **whether the we can see image in the list:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681007682067/1be75aa9-b664-42f0-a704-2d8a8f1a78ee.png align="center")

**Since, we have an image now, lets run a container using the docker image:**

`docker run -d -p 9000:9000 react-notes-app:latest`

**Your docker container will be ready, check using** `docker ps`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681007967128/628f02bd-0826-4136-b7ab-315cc993b797.png align="center")

**But now, we dont want to expose our public ip in the browser, but we want to serve it to the user using reverse proxy and route it through nginx.**

**To check whether your application is working on local host,**

`curl -L http:127.0.0.1:9000`

**Now we need to make changes to nginx configuration. For that,**

`cd`

`cd /etc/nginx/sites-enabled`

**You will see a default file:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681009401724/2b589d2b-d85a-4f67-8d8c-0b07ed7235c7.png align="center")

**now edit the default file using vim editor. Since, we will not have user permissions to access it, use sudo**

`sudo vim default`

**edit the location part on default file and add this below** `location / {` **:**

`proxy_pass http://127.0.0.1:9000;`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681009845506/0cd0227a-950e-4a2f-bc82-f865aeb10c28.png align="center")

**Now save the file.**

**After this, we need to restart nginx**

**go in django-todo-app&gt;mynotes-build and copy the static folder to /var/www/html**

`cp static /var/www/html`

**Now just copy the public IP to the browser and you will see your page is running**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681050433300/4a20ac26-67de-4e8d-a16e-7de468208d54.png align="center")