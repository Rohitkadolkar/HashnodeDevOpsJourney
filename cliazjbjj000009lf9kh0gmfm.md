---
title: "#Day32 : Launching your Kubernetes Cluster with Deployment"
datePublished: Wed May 31 2023 00:44:37 GMT+0000 (Coordinated Universal Time)
cuid: cliazjbjj000009lf9kh0gmfm
slug: day32-launching-your-kubernetes-cluster-with-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685493850725/8a10501f-af80-43db-8b13-4ff425b0db00.png
tags: kubernetes, devops

---

### What is Deployment in k8s

A Deployment provides a configuration for updates for Pods and ReplicaSets.

You describe a desired state in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate. You can define Deployments to create new replicas for scaling, or to remove existing Deployments and adopt all their resources with new Deployments.

## Task-1:

**Create one Deployment file to deploy a sample todo-app on K8s using "Auto-healing" and "Auto-Scaling" feature**

* add a deployment.yml file (sample is kept in the folder for your reference)
    

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: todo
  template:
    metadata:
      labels:
        app: todo
    spec:
      containers:
      - name: todo
        image: rishikeshops/todo-app
        ports:
        - containerPort: 3000
      # remove autoscaling from here
  autoscaling:
    enabled: true
    minReplicas: 2
    maxReplicas: 10
    targetCPUUtilizationPercentage: 50
```

* apply the deployment to your k8s (kubeadm) cluster by command `kubectl apply -f deployment.yml`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682591360126/de975acb-a682-4afd-b797-c1f4b2971d81.png?auto=compress,format&format=webp align="left")

Verify it on node:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682591379241/894c0f78-65ab-4b63-b3c9-55c7f453ed7d.png?auto=compress,format&format=webp align="left")

### **Detailed View of this code:**

Here's a detailed explanation of the YAML file using stickers:

🔄 `apiVersion: apps/v1`: This line specifies the Kubernetes API version that this deployment will use.

📌 `kind: Deployment`: This line specifies that this YAML file defines a deployment object in Kubernetes. Deployments are used to manage and scale containerized applications.

📝 `metadata: name: todo-app`: This section specifies the metadata for the deployment object, including its name. In this case, the deployment is named "todo-app".

📝 `spec: replicas: 2`: The "spec" section of the YAML file specifies the desired state of the deployment. In this case, we want to run two replicas of the application.

🔎 `selector: matchLabels: app: todo`: This section specifies the label selector for the deployment. It uses the label "app: todo" to match the pods that belong to this deployment.

📝 `template: metadata: labels: app: todo`: This section specifies the pod template for the deployment. It sets the "app" label to "todo".

📝 `spec: containers: - name: todo image: rishikeshops/todo-app ports: - containerPort: 3000`: This section specifies the container configuration for the deployment. It defines a single container named "todo" with the specified image and port number.

📝 `autoscaling: enabled: true minReplicas: 2 maxReplicas: 10 targetCPUUtilizationPercentage: 50`: This section specifies the autoscaling configuration for the deployment. When enabled, it will automatically adjust the number of replicas based on CPU utilization. The minimum number of replicas is 2 and the maximum number is 10. The target CPU utilization percentage is set to 50.

🚀 Overall, this YAML file defines a scalable deployment for a todo app running in Kubernetes. By using the autoscaling feature, the deployment can automatically adjust the number of replicas based on demand, ensuring that the application is always available and responsive to users.