## KUBERNETES COMMANDS : CORE CONCEPTS

### **QUIZ 1** PRACTICE TEST – PODS

---

- How many pods exist on the system? In the current(default) namespace.

      kubectl get pods

- Create a new pod with the nginx image.

      kubectl run nginx --image=nginx

- What is the image used to create the new pods? You must look at one of the new pods in detail to figure this out.

      kubectl describe pod newpods-<id>

- How many containers are part of the pod webapp?

      kubectl describe pod webapp

- Delete the webapp Pod.

      kubectl delete pod webapp

- Create a new pod with the name redis and with the image redis123.Use a pod-definition YAML file. And yes the image name is wrong!

      kubectl run redis --image=redis123 --dry-run=client -o yaml > redis-definition.yaml

- Now change the image on this pod to redis.

      kubectl edit pod redis

<p>&nbsp;</p>

### **QUIZ 2** PRACTICE TEST – REPLICASETS

---

- How many ReplicaSets exist on the system? In the current(default) namespace.

      kubectl get replicaset

- What is the image used to create the pods in the new-replica-set?

      kubectl describe replicaset

- Create a ReplicaSet using the replicaset-definition-1.yaml file located at /root/. There is an issue with the file, so try to fix it.

      kubectl create -f /root/replicaset-definition-1.yaml

- Fix the issue in the replicaset-definition-2.yaml file and create a ReplicaSet using it. This file is located at /root/

      https://github.com/chandu42242682/KUBERNETES/blob/main/replicaset-definition-2.yaml

- Delete the two newly created ReplicaSets - replicaset-1 and replicaset-2

      kubectl delete replicaset <replicaset-name>

- Scale the ReplicaSet to 5 PODs. Use kubectl scale command or edit the replicaset using kubectl edit replicaset.

      kubectl edit replicaset new-replica-set

      kubectl scale rs new-replica-set --replicas=5

<p>&nbsp;</p>

### **QUIZ 3** PRACTICE TESTS – DEPLOYMENTS

---

- How many Deployments exist on the system? In the current(default) namespace.

      kubectl get deployment

- What is the image used to create the pods in the new deployment?

      kubectl describe deployment <deployment-name>

- Create a new Deployment with the below attributes using your own deployment definition file.

  Name: httpd-frontend

  Replicas: 3

  Image: httpd:2.4-alpine

      https://github.com/chandu42242682/KUBERNETES/blob/main/deployment-definition-httpd.yaml

<p>&nbsp;</p>

### **QUIZ 4** PRACTICE TEST NAMESPACES

---

- How many Namespaces exist on the system?

      kubectl get ns --no-headers | wc -l

- How many pods exist in the research namespace?

      kubectl -n research get pods --no-headers | wc -l

- Create a POD in the finance namespace. Use the spec given below.

  Name: redis

  Image Name: redis

      kubectl run redis --image=redis -n finance

- Which namespace has the blue pod in it?

      kubectl get pods --all-namespaces | grep blue

<p>&nbsp;</p>

### **QUIZ 5** PRACTICE TEST SERVICES

---

- How many Services exist on the system? in the current(default) namespace

      kubectl get service

- What is the targetPort configured on the kubernetes service?

      kubectl describe service

- Create a new service to access the web application using the service-definition-1.yaml file

  Name: webapp-service

  Type: NodePort

  targetPort: 8080

  port: 8080

  nodePort: 30080

  selector: simple-webapp

      https://github.com/chandu42242682/KUBERNETES/blob/main/service-definition-1.yaml

<p>&nbsp;</p>

### **QUIZ 6** PRACTICE TEST – IMPERATIVE COMMANDS

---

- Deploy a pod named nginx-pod using the nginx:alpine image. Use imperative commands only.

      kubectl run nginx-pod --image=nginx:alpine

- Deploy a redis pod using the redis:alpine image with the labels set to tier=db. Either use imperative commands to create the pod with the labels. Or else use imperative commands to generate the pod definition file, then add the labels before creating the pod using the file.

      kubectl run redis --image=redis:alpine --dry-run=client -oyaml > redis-pod.yaml

      https://github.com/chandu42242682/KUBERNETES/blob/main/redis-pod.yaml

- Create a service redis-service to expose the redis application within the cluster on port 6379. Use imperative commands.

      kubectl expose pod redis --port=6379 --name redis-service

- Create a deployment named webapp using the image kodekloud/webapp-color with 3 replicas. Try to use imperative commands only. Do not create definition files.

      kubectl create deployment webapp --image=kodekloud/webapp-color --replicas=3

- Create a new pod called custom-nginx using the nginx image and expose it on container port 8080.

      kubectl run custom-nginx --image=nginx --port=8080

- Create a new namespace called dev-ns. Use imperative commands.

      kubectl create namespace dev-ns

- Create a new deployment called redis-deploy in the dev-ns namespace with the redis image. It should have 2 replicas. Use imperative commands.

      kubectl create deployment redis-deploy --image=redis --replicas=2 -n dev-ns

- Create a pod called httpd using the image httpd:alpine in the default namespace. Next, create a service of type ClusterIP by the same name (httpd). The target port for the service should be 80. Try to do this with as few steps as possible.

      kubectl run httpd --image=httpd:alpine --port=80 --expose




