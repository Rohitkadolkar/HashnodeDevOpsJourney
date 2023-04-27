---
title: "#Day22 : Getting Started with Jenkins 😃"
datePublished: Thu Apr 27 2023 21:22:14 GMT+0000 (Coordinated Universal Time)
cuid: clgzmry1t000g09lebj8e5k1v
slug: day22-getting-started-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682630625473/871a802c-6a00-4bae-99ad-8cdedfdb9d8d.jpeg
tags: devops, jenkins

---

## What is Jenkins?

* Jenkins is an open source continuous integration-continuous delivery and deployment (CI/CD) automation software DevOps tool written in the Java programming language. It is used to implement CI/CD workflows, called pipelines.
    
* Jenkins is a tool that is used for automation, and it is an open-source server that allows all the developers to build, test and deploy software. It works or runs on java as it is written in java. By using Jenkins we can make a continuous integration of projects(jobs) or end-to-endpoint automation.
    
* Jenkins achieves Continuous Integration with the help of plugins. Plugins allow the integration of Various DevOps stages. If you want to integrate a particular tool, you need to install the plugins for that tool. For example Git, Maven 2 project, Amazon EC2, HTML publisher etc.
    

**Let us do discuss the necessity of this tool before going ahead to the procedural part for installation:**

* Nowadays, humans are becoming lazy😴 day by day so even having digital screens and just one click button in front of us then also need some automation.
    
* Here, I’m referring to that part of automation where we need not have to look upon a process(here called a job) for completion and after it doing another job. For that, we have Jenkins with us.
    

Note: By now Jenkins should be installed on your machine(as it was a part of previous tasks, if not follow [https://hashnode.com/post/clfolv6fg000409mj8kswejpe](https://hashnode.com/post/clfolv6fg000409mj8kswejpe)

## Tasks:

**1\. What you understood in Jenkin, write a small article in your own words (Don't copy from Internet Directly)**

Jenkins is a tool used for building CI/CD pipelines. CI/CD stands for Continuous integration and Continuous deployment. It consists of automating the integration process by completing the code integration stages of the SDLC that are Planning, Design and Development. The later part includes completing the SDLC by also automating the Testing and deployment part using different tools like docker and Kubernetes and all this can be done without even a single click. The code on Github can be directly linked to Jenkins using Webhook and the changes made on Github directly trigger a new build on Jenkins to the agent server. Thus it keeps the process of deployment continuous without a single click.

**2.Create a freestyle pipeline to print "Hello World!!**

Once Jenkins is setup, go to Dashboard

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682629528492/46bed134-4c28-4ba9-b3a2-48545577909f.png align="center")

In dashboard, select new item,

Enter name as First Jenkins project and select freestyle

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682629604473/31e7a36a-e28e-4774-a0fb-f6b9ffe541d3.png align="center")

Give description and select none in source code management

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682629903046/b1e9b0ce-f471-4696-81eb-32cb846faec5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682629910722/22dda64d-1dcc-4a26-8dae-012114602acf.png align="center")

In build steps, select execute shell and type `echo "Hello World"`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682630239528/14d0c32e-a46c-4dd0-ba3e-f995083642ef.png align="center")

Now go to dashboard &gt; my first project and click build

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682630262192/54b8d98c-76bf-4190-9d7b-eb7e0b63838b.png align="center")

Go to build#1 in left pane

Go to console output, you will see the command running!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682630314058/d104839a-0b15-4189-9c49-d8244af97680.png align="center")