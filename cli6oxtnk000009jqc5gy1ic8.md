---
title: "#Day31 : Launching your First Kubernetes Cluster with Nginx running"
datePublished: Sun May 28 2023 00:36:53 GMT+0000 (Coordinated Universal Time)
cuid: cli6oxtnk000009jqc5gy1ic8
slug: day31-launching-your-first-kubernetes-cluster-with-nginx-running
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685234123896/1be8716c-7190-4149-b4a5-91d05f015236.jpeg
tags: kubernetes, devops, kubernetes-pods

---

## How Kubernetes makes deployment easier

With Kubernetes, organizations can achieve increased efficiency and agility in their development and deployment processes, resulting in faster time to market and reduced operational costs. Kubernetes also provides a high degree of **scalability**, allowing organizations to scale their applications as their business grows and evolves easily.

## Setting up Master and Node in Kubernetes

**Pre-requisites**

For the master node, if you are using an AWS instance, you will require a t2.medium instance as you will need two CPUs to run kubeadm.

For worker node, it is ok if we use t2.micro instance.

**Setup**

Launch both instances or ssh into the instances, whatever is convenient.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685231199482/c33cd2c3-f1cb-4689-a1ec-ec4f567b5c83.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685231285233/78de25bf-f6a0-4091-a20c-bb19d70a15f1.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685231406219/cd52a178-e109-402d-9462-3afe52febe16.png align="center")

Now Install docker on both Master and node.

```bash
sudo apt install docker.io -y

sudo systemctl start docker
sudo systemctl enable docker
```

Also install kubeadm on both master and node.

```bash
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg

echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
```

Update the system

```bash
sudo apt update -y
```

Install Kubeadm,Kubectl and Kubelet in both Master and Node.

```bash
sudo apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y
```

Now, on both master and node, gain in superuser access

`sudo su`

Now in master, run kubeadm

`kubeadm init`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685231765077/57567b23-705a-4500-9371-91a78802c45b.png align="center")

Now, run in master

`export KUBECONFIG=/etc/kubernetes/admin.conf`

To finish Master setup,

`kubectl apply -f` [`https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml`](https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml)

```bash
kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
```

Call kubeadm to create token for node connection:

`kubeadm token create --print-join-command`

It will give us a token. Copy this token and take it to worker node and paste it there.

Your node will be connected to the master.

To check, go to master and type

`kubectl get nodes`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685232941691/284bf215-80b2-426e-a897-41ad5c3a00b6.png align="center")

## Running a pod

![Kubernetes Pod Logo](https://th.bing.com/th?q=Kubernetes+Pod+Logo&w=120&h=120&c=1&rs=1&qlt=90&cb=1&dpr=1.5&pid=InlineBlock&mkt=en-IN&cc=IN&setlang=en&adlt=moderate&t=1&mw=247 align="left")

Running a Pod on Kubernetes is pretty easy

```bash
kubectl run nginx --image=nginx
```

By default, the `kubectl run` command creates a deployment and a replica set along with the pod. If you only want to create a pod without creating a deployment or replica set, you can use the `--restart=Never` flag:

```bash
kubectl run nginx --image=nginx --restart=Never
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685233160818/1129ef30-ff57-46c2-8354-2aa5a4093011.png align="center")

Now, go to worker node and check whether pod is up -

`docker ps`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685233258933/55144502-f8fe-4b4c-8363-8870390d319a.png align="center")

To check pods, in master

`kubectl get pods`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685233323304/04e39201-4ce4-488c-bac9-42fb28952071.png align="center")

To delete pod

`kubectl delete pod nginx`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685233383794/f297afc6-428c-4dcd-b11f-906d67bde9b4.png align="center")

We can also create a new pod from an image from docker hub using a YAML file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685233456695/4a41a5af-530c-41cf-aecb-803fc288a716.png align="center")

To run it, on master node:

`kubectl apply -f pod.yml`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685233824852/236c81fc-f3a0-4c46-af64-d0ae45750f2d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685234041288/4f1b9ca8-9bfc-4f04-b3f0-3f4ca12812e6.png align="center")