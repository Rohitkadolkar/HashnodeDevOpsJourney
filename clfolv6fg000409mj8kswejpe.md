---
title: "#Day7 #90DaysofDevOps Understanding Package Manager and Systemctl:"
datePublished: Sat Mar 25 2023 23:31:35 GMT+0000 (Coordinated Universal Time)
cuid: clfolv6fg000409mj8kswejpe
slug: day7-90daysofdevops-understanding-package-manager-and-systemctl
tags: linux, devops, package-management

---

### What is a package manager in Linux?

In simpler words, a package manager is a tool that allows users to install, remove, upgrade, configure and manage software packages on an operating system. The package manager can be a graphical application like a software center or a command line tool like apt-get or pacman.

### What is a package?

A package is usually referred to an application but it could be a GUI application, command line tool or a software library (required by other software programs). A package is essentially an archive file containing the binary executable, configuration file and sometimes information about the dependencies.

### Different kinds of package managers

Package Managers differ based on packaging system but same packaging system may have more than one package manager.

For example, RPM has Yum and DNF package managers. For DEB, you have apt-get, aptitude command line based package managers.

### How to install Docker

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679786548724/9efce528-8d5f-4dc0-9afa-7ce4336fee66.png align="center")

1. **Remove docker if already installed**
    
    `sudo apt-get remove docker docker-engine` [`docker.io`](http://docker.io)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679768813784/be637364-9cc8-4b5c-81d6-6cf0e74a751d.png align="left")
    
2. **Update package list**
    

`sudo apt-get update`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679768126167/d99467e1-6e70-4060-b990-92b1ee406539.png align="center")

1. **Install Docker package**
    

`sudo apt install` [`docker.io`](http://docker.io)

1. **Install dependency packages**
    

`sudo snap install docker`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679769957626/1d56114f-edb4-481b-9cda-837420554468.png align="center")

1. **Check version of docker**
    

`docker -- version`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679770097265/43204c92-aa54-4ce7-a73f-a069c8698ed6.png align="center")

1. **Pull an image from docker hub using following command**
    

`sudo docker run hello-world`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679770357658/ac0c0874-7f1f-4a8a-9130-c1bbbcb094d4.png align="center")

1. **Check if docker image has been pulled and is present in the system**
    

`sudo docker images`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679770439936/34f77a16-2f9e-438f-a54b-e2da1300c4e4.png align="center")

1. **To display all the containers pulled, use following**
    

`sudo docker ps -a`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679770570445/1d0ff573-cd69-4e64-b427-e11c2af6a903.png align="center")

1. **To check containers in running state, use following**
    

`sudo docker ps`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679770633977/8f8739fb-9c4c-498e-bae9-cbcf269333a1.png align="center")

### How to install Jenkins

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679786575399/d6e90922-8fad-4b32-96f8-f25ce0d26071.png align="center")

1. **Install Java**
    
    `sudo apt-cache search openjdk`
    
    `sudo apt-get install openjdk-11-jre -y`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679772829216/5d1a02df-95c9-4d32-a963-6f697e749a26.png align="center")

1. **Check Java version**
    
    `java --version`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679772899595/71023947-056f-465c-a6fe-0f33bd24923c.png align="center")

1. **Update package list**
    

`sudo apt update`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679768126167/d99467e1-6e70-4060-b990-92b1ee406539.png align="center")

1. **Add the repository key to the system:**
    

`wget -q -O -` [`https://pkg.jenkins.io/debian-stable/jenkins.io.key`](https://pkg.jenkins.io/debian-stable/jenkins.io.key) `| sudo apt-key add -`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679771978246/ef9be5c7-e193-40ec-82a9-003ffa3e4268.png align="center")

1. **Next, let’s append the Debian package repository address to the server’s** `sources.list`**:**
    

`sudo sh -c 'echo deb` [`http://pkg.jenkins.io/debian-stable`](http://pkg.jenkins.io/debian-stable) `binary/ > /etc/apt/sources.list.d/jenkins.list'`

1. **After both commands have been entered, we’ll run** `update` **so that** `apt` **will use the new repository**
    

`sudo apt update`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679772055323/8aed134b-b00b-4d69-9c1c-dd3d385417f4.png align="center")

1. **Finally, we’ll install Jenkins and its dependencies.**
    

`sudo apt install jenkins`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679773270357/f4274196-65b1-4bb6-aaa0-e6abb06c438b.png align="center")

1. Starting jenkins
    

`sudo systemctl start jenkins`

1. Since `systemctl` doesn’t display status output, we’ll use the `status` command to verify that Jenkins started successfully:
    

`sudo systemctl status jenkins`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679773617700/6859c965-5afe-43bf-954d-05775f4204c1.png align="center")

1. Opening the Firewall port 8080
    

`sudo ufw allow 8080`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679773891137/5432fab5-1ac9-47be-bb0c-1040726e18fb.png align="center")

1. Check status
    

`sudo ufw status`

1. If status is inactive
    

`sudo ufw allow OpenSSH`

`sudo ufw enable`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679774367896/7e0ac59d-5cbf-481b-90a9-d5c0a1ee8e00.png align="center")

1. Check status again
    

`sudo ufw status`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679774416573/74a1b0a6-cd67-48e0-affa-9aecee6d6f73.png align="center")

1. Setting up Jenkins
    

To set up your installation, visit Jenkins on its default port, `8080`, using your server domain name or IP address: [`http://your_server_ip_or_domain:8080`](http://your_server_ip_or_domain:8080)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679777699332/909eb904-4078-4ba6-b066-0f9fc529f75f.png align="center")

1. **Here It will ask for a password to log in as path of the password is highlighted in red colour just copy it and paste into your browser:**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679777893150/f94b3dd2-5f4d-4862-ad04-d8f4f11bae46.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679778464384/98f3cbb7-8751-4bc7-aedf-c70bd4995960.png align="center")

## **systemctl and system:**

* Systemd is a system and service manager, while systemctl is a command-line utility for managing system services.
    
* Systemd provides a suite of daemons, libraries, and utilities to manage system components, while systemctl is a specific tool within that suite.
    

## **check the status of the docker service in your system:**

Check the status of the Docker service on your Linux system using the following command in the terminal:

sudo systemctl status docker

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679778666389/e0973221-155b-451e-8a2b-883ff8211822.png align="center")

**To Stop the Service:**

To stop the Docker service, you can use the following command in the terminal:

sudo systemctl stop docker

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679778788111/6e27f6d6-c015-4996-a3b3-beb21fded4a1.png align="center")

This will stop the Docker service immediately. If you want to prevent the service from starting automatically at boot, you can also disable it using the following command:

sudo systemctl disable docker

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679779541393/95431694-cf63-477a-b3fc-a2dc3e3b6a44.png align="center")

### **check the status of Jenkins service in your system:**

`sudo systemctl status jenkins`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679778921981/acca25c5-d345-460c-ae52-6ba01f798342.png align="center")

### **To Stop the Service:**

To stop the Jenkins service, you can use the following command in the terminal:

`sudo systemctl stop jenkins`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679779380191/cb233723-52e1-4537-9cdd-1eadb5dbf00a.png align="center")

### systemctl

The systemctl command **manages both system and service configurations, enabling administrators to manage the OS and control the status of services**. Further, systemctl is useful for troubleshooting and basic performance tuning.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679779818055/10a2d228-90f8-41f3-b1f0-39253c466c00.png align="center")

### **service**

The service command **starts, stop and restart a daemon or services by calling the script**. Usually all scripts are stored in /etc/init. d directory. It runs a script in as predictable environment as possible.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679779966526/533bae6b-8f8b-4ec2-8223-f9e10632c8af.png align="center")

### systemctl vs service

**systemctl is basically a more powerful version of service**. With service you can only do commands related to the service (i.e. status, reload, restart) whereas with systemctl you can use more advanced commands such as: systemctl is-failed name.service # check if service failed to load