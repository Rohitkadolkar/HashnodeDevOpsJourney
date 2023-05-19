---
title: "#Day26 and #Day27 Task: Jenkins Declarative Pipeline"
datePublished: Fri May 19 2023 21:54:14 GMT+0000 (Coordinated Universal Time)
cuid: clhv3lty2000909me7y1dgu7o
slug: day26-and-day27-task-jenkins-declarative-pipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684533215656/a7347443-c030-4d9d-a9b2-b890bc34da47.png
tags: docker, devops, jenkins

---

One of the most important parts of your DevOps and CICD journey is a Declarative Pipeline Syntax of Jenkins

## Some terms for your Knowledge

**What is Pipeline -** A pipeline is a collection of steps or jobs interlinked in a sequence.

**Declarative:** Declarative is a more recent and advanced implementation of a pipeline as a code.

**Scripted:** Scripted was the first and most traditional implementation of the pipeline as a code in Jenkins. It was designed as a general-purpose DSL (Domain Specific Language) built with Groovy.

# Why you should have a Pipeline

The definition of a Jenkins Pipeline is written into a text file (called a [`Jenkinsfile`](https://www.jenkins.io/doc/book/pipeline/jenkinsfile)) which in turn can be committed to a project’s source control repository.  
This is the foundation of "Pipeline-as-code"; treating the CD pipeline as a part of the application to be versioned and reviewed like any other code.

**Creating a** `Jenkinsfile` and committing it to source control provides a number of immediate benefits:

* Automatically creates a Pipeline build process for all branches and pull requests.
    
* Code review/iteration on the Pipeline (along with the remaining source code).
    

# Pipeline syntax

```yaml
pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                // 
            }
        }
        stage('Test') { 
            steps {
                // 
            }
        }
        stage('Deploy') { 
            steps {
                // 
            }
        }
    }
}
```

# Pre-steps

First go to

Jenkins dashboard

Select Manage Jenkins

Under security, select **Manage credentials**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684530582510/b2218937-4aca-40a6-91fe-b62828e3005c.png align="center")

In System global add credentials for Docker so that we can push and pull images from docker-hub by logging in.

Also add Webhook to GitHub repository

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684530818358/02648e92-6af7-41ce-bf98-9d5b60a13d49.png align="left")

Go to the repository&gt;Settings&gt;Webhook(left pane)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684530979671/5e9e7a09-ad50-4fc0-bf0d-73dd80cbaf4f.png align="center")

## Steps to build pipeline

Go to New item on dashboard

Give a name (My-First-Pipeline)

Give description

Check Github Project and enter url

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684531172872/49035492-a60b-433e-a3ab-aaff46703f00.png align="center")

Under build triggers, select **GitHub hook trigger for GITScm polling**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684531241536/543dce13-b1cf-4a0d-ac80-448bdaa5ad86.png align="center")

Enter pipeline script as follows -

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684532316020/845f8be8-837d-4d99-9504-6f4a7a15e606.png align="center")

Now go to the pipeline from dashboard and run build now

It will show build stepwise

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684532877269/fa3d48dd-20a5-4383-9a00-9ad27a72ca02.png align="center")

## Webhook

Suppose you make some changes in your Github code, You do not need to build again manually.

Using webhook, a build will immediately be triggered as soon as a push is made on the master branch.

Now lets make some changes on the Github code.

As soon as I make some changes, a build will automatically be triggered as shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684532858926/a5248cc2-54d5-4aba-8168-e0718145cc92.png align="center")