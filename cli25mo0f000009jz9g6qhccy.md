---
title: "#Day28 : Jenkins Agents #90DaysofDevOps"
datePublished: Wed May 24 2023 20:25:16 GMT+0000 (Coordinated Universal Time)
cuid: cli25mo0f000009jz9g6qhccy
slug: day28-jenkins-agents-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684959866402/0d686f83-6b00-467d-bcee-a035c792d43a.png
tags: docker, devops, jenkins

---

# Jenkins Master (Server)

Jenkins’s server or master node holds all key configurations. Jenkins master server is like a control server that orchestrates all the workflow defined in the pipelines. For example, scheduling a job, monitoring the jobs, etc.

# Jenkins Agent

An agent is typically a machine or container that connects to a Jenkins master and this agent that actually execute all the steps mentioned in a Job. When you create a Jenkins job, you have to assign an agent to it. Every agent has a label as a unique identifier.

When you trigger a Jenkins job from the master, the actual execution happens on the agent node that is configured in the job.

A single, monolithic Jenkins installation can work great for a small team with a relatively small number of projects. As your needs grow, however, it often becomes necessary to scale up. Jenkins provides a way to do this called “master to agent connection.” Instead of serving the Jenkins UI and running build jobs all on a single system, you can provide Jenkins with agents to handle the execution of jobs while the master serves the Jenkins UI and acts as a control node.

![](https://user-images.githubusercontent.com/115981550/215276859-fa140ab7-e905-41c9-8ae2-1eef577c5e72.png align="left")

## Pre-requisites

Let’s say we’re starting with a fresh Ubuntu 22.04 Linux installation. To get an agent working make sure you install Java ( same version as jenkins master server ) and Docker on it.

`Note:- While creating an agent, be sure to separate rights, permissions, and ownership for jenkins users.`

**Step 1**

Launch two instances, one agent and master server

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684952218332/5bad0e75-90b8-43b8-9a76-fdfca80d5709.png align="center")

These are the two servers, Master and Agent

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684952368219/f3d5afeb-4afc-4c9a-a9dd-e1bd0bebccb2.png align="center")

**Step 2**

1. Install Java on Jenkins on Master and Agent
    
2. Install Jenkins on Master and Agent
    
3. Install Docker on Agent server
    

**Step 3**

Once, both servers are setup, we need to make sure the agent server can be connected from within Master server.

For this,

In the master instance, go to

`cd .ssh/`

Now type

`ssh-keygen`

Press enter key will be generated in id\_rsa.pub

Now

`cat id_rsa.pub`

This will give us a public key of master

Copy the public key and go to agent server

Now, in agent server,

`cd .ssh/`

`vim auth_keys`

and paste the copied public key and save.

Now go back to agent server and type

`ssh ubuntu@<agentserver-publicip>`

You will directly connect to server

**Step 4**

Now lets create a agent on Jenkins GUI

Give node name.

Give name, desc, remote-root-dir(/home/ubuntu)

Give label as application to use in that server

Give usage details(as much as possible)

Give launch method ssh

in host give public ip of agent server

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684958271537/47ec91ec-50e0-4d29-b37d-b9ee7f25e189.png align="center")

In credentials click add

In kind select ssh username with pvt key

In ID (dev-ssh-key)

Put description. Put username as ubuntu

Now in private key section, fetch id\_rsa from jenkins master server and paste in private key

in known host verification, select non-verifying verification strategy.

Now save, open check and check, your agent is running

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684959389759/c61b10b3-87f1-4b4c-9c64-cae59e8aa6cc.png align="center")

**Step 5**

Now create a Pipeline and run it on Node server.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682155772638/15eeeb3c-ddfa-4396-b712-44185bb4b1fd.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682155719803/b1b01963-8899-409a-a89a-f78f6fb0f277.png?auto=compress,format&format=webp align="left")