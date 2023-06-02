---
title: "#Day33 : Working with Namespaces and Services in Kubernetes"
datePublished: Fri Jun 02 2023 00:46:38 GMT+0000 (Coordinated Universal Time)
cuid: cliduhm1u000609ml6cya0x2z
slug: day33-working-with-namespaces-and-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685666888926/aac86a08-c5a9-4c78-a6c0-ddaf3eefe545.png
tags: kubernetes, devops

---

## What are Namespaces and Services in k8s

In Kubernetes, Namespaces are used to create isolated environments for resources. Each Namespace is like a separate cluster within the same physical cluster. Services are used to expose your Pods and Deployments to the network. Read more about Namespace.

# Today's task:

## Task 1:

* Create a Namespace for your Deployment. Use the command `kubectl create namespace <namespace-name>` to create a Namespace
    

`kubectl create namespace <namespacename>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685665892627/d4d26d3f-2a22-4863-a961-38b288655a41.png align="center")

* Update the deployment.yml file to include the Namespace
    

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: django-todo-deployment
  namespace: django-todo-ns
  labels:
    app: django-todo
spec:
  replicas: 2
  selector:
    matchLabels:
      app: django-todo
  template:
    metadata:
      labels:
        app: django-todo
    spec:
      containers:
      - name: django-todo
        image: trainwithshubham/django-todo:latest
        ports:
        - containerPort: 8000
```

* Apply the updated deployment using the command: `kubectl apply -f deployment.yml -n <namespace-name>`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685666087756/bd97a44c-f8d3-497e-9929-a9e861f3d78d.png align="center")

* Verify that the Namespace has been created by checking the status of the Namespaces in your cluster.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685666142250/de6da41d-1f27-43fa-be94-536d741c6a12.png align="center")

## Task 2:

* Read about Services, Load Balancing, and Networking in Kubernetes. Refer official documentation of kubernetes.
    

## **Task 2:**

Here are some general reasons why Services are used in Kubernetes:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682593361542/4ec86388-4eda-4fe0-96fa-5fac9ac535fb.png?auto=compress,format&format=webp align="left")

1. Load balancing: Services provide load balancing across multiple instances of a Pod or multiple Pods, enabling high availability and scalability of an application.
    
2. Service discovery: Services allow clients to discover the endpoints of a set of Pods, abstracting away the complexity of individual Pod management.
    
3. Networking: Services provide network connectivity between Pods and other services within a Kubernetes cluster, making it easier to manage network traffic and communication between components.
    
4. Health checks: Services can monitor the health of the Pods they are load balancing traffic to, and remove any unhealthy Pods from the pool. This ensures that traffic is only sent to healthy Pods, improving the overall reliability of the application.
    
5. IP address management: Services provide a stable IP address and DNS name for a set of Pods, which can be used by external clients to access the application. This allows you to abstract away the underlying infrastructure and focus on the logical components of your application.
    

### NodePort:

A NodePort service exposes a set of pods to the outside world by opening a specific port on each node in the cluster. Any traffic that is sent to that port on any node will be forwarded to the corresponding pods. NodePort services are often used when you need to expose a service to the public internet or to external clients.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-nodeport-service
spec:
  type: NodePort
  selector:
    app: my-app
  ports:
    - name: http
      port: 80
      targetPort: 8080
      nodePort: 30000
```

### ClusterIP:

A ClusterIP service, on the other hand, exposes a set of pods internally within the cluster. It assigns a unique IP address to the service and load balances traffic among the pods. ClusterIP services are typically used for internal communication between pods within the cluster or for exposing services to other services within the same cluster.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-clusterip-service
spec:
  type: ClusterIP
  selector:
    app: my-app
  ports:
    - name: http
      port: 80
      targetPort: 8080
```