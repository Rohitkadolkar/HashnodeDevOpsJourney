---
title: "#Day34 : Working with Services in Kubernetes"
datePublished: Tue Jun 06 2023 23:27:25 GMT+0000 (Coordinated Universal Time)
cuid: clikwv00c00050albcxb3ev0i
slug: day34-working-with-services-in-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686094024410/bc159991-c6e9-42a4-bc89-050db3ab38b1.png
tags: kubernetes, devops

---

## What are Services in K8s

In Kubernetes, Services are objects that provide stable network identities to Pods and abstract away the details of Pod IP addresses. Services allow Pods to receive traffic from other Pods, Services, and external clients.

## Task-1:

![Load Balancing on Kubernetes](https://www.nerdcoding.org/post/2018/img/2018-05-11-NodePort-Service.png align="left")

* Create a Service for your todo-app Deployment from Day-32
    
* Create a Service definition for your todo-app Deployment in a YAML file.
    

```yaml
apiVersion: v1
kind: Service
metadata:
  name: django-todo-service
  namespace: django-todo-ns
spec:
  type: NodePort
  selector:
    app: django-todo
  ports:
      # By default and for convenience, the `targetPort` is set to the same value as the `port` field.
    - port: 80
      targetPort: 8000
      # Optional field
      # By default and for convenience, the Kubernetes control plane will allocate a port from a range (default: 30000-32767)
      nodePort: 30007
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685833418660/1a84212e-d5a5-4b99-855e-95398ec6b3e7.png align="center")

* Apply the Service definition to your K8s (minikube) cluster using the `kubectl apply -f service.yml -n <namespace-name>` command.
    

```yaml
kubectl apply -f service.yml -n django-todo-ns
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685833563744/cd0992e6-ea85-4f26-a5ac-b2f763599807.png align="center")

* Verify that the Service is working by accessing the todo-app using the Service's IP and Port in your Namespace.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685833610632/9adb11ed-5f87-4fd1-9f3e-a24d9f64dd38.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685834022965/51efe363-ba2e-43d1-ad8e-fa4bd6435e90.png align="center")

## Task-2:

* Create a ClusterIP Service for accessing the todo-app from within the cluster
    
* Create a ClusterIP Service definition for your todo-app Deployment in a YAML file.
    
* Apply the ClusterIP Service definition to your K8s (minikube) cluster using the `kubectl apply -f cluster-ip-service.yml -n <namespace-name>` command.
    
* Verify that the ClusterIP Service is working by accessing the todo-app from another Pod in the cluster in your Namespace.
    

![Kubernetes Services Explained with Examples](https://1.bp.blogspot.com/-_z2PXrCNi8E/XrVfhrACxII/AAAAAAAABv4/19Z84lEt7sI2Ey6vEe_MgC2dfQRuIvjigCLcBGAsYHQ/s1600/kubernetes%2Bclusterip%2Bexamples.JPG align="left")

Create file `vim cluster-ip-service.yml`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686093627880/f7469052-2dbf-4757-9f0d-80a9608b61b9.png align="center")

Apply `kubectl apply -f cluster-ip-service.yml`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686093671126/4f508ff8-61f3-42a5-9c85-226c351bc61e.png align="center")

Check whether service is running -

kubectl get svc -n django-todo-ns

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1686093730669/a2e2c937-d96e-47e3-b4ce-ce2e13daf781.png align="center")

Step-4 Deploy another Pod in the `django-todo-ns` namespace to test the service. You can use the following YAML definition to create a simple Pod:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: test-pod
  namespace: django-todo-ns
spec:
  containers:
  - name: busybox
    image: busybox
    command: ['sh', '-c', 'while true; do wget -q -O- django-todo-cluster-ip-service:8000; done']
```

This Pod runs a simple `busybox` container that repeatedly accesses the `todo-app` service using `wget`. The Pod should be able to access the `django-todo-cluster-ip-service` service using its name and port number.

Apply the Pod definition using the following command:

```yaml
kubectl apply -f test-pod.yml -n django-todo-ns
```

Now execute the pod

```yaml
kubectl exec -it test-pod -n django-todo-ns -- /bin/sh
```

Test Todo app

```yaml
wget -qO- http://10.96.190.151:8000
```

Now you sucessfuly Access it through another Port