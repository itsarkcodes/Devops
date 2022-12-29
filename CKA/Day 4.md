# Kube Proxy
- Kube-proxy is a process that runs on each node in the Kubernetes cluster.
- Its job is to look for new services, and every time a new service is created, it creates the appropriate rules on each node to forward traffic to those services to the backend pods.

# PODS
- Kubernetes does not deploy containers directly on the worker nodes.
- The containers are encapsulated into a Kubernetes object known as pods.
- A pod is a single instance of an applicatio.
- A pod is the smallest object that you can create in Kubernetes.
- 
![image](https://user-images.githubusercontent.com/87442305/209912379-03a12226-0f11-41ef-8a22-955288a419fe.png)

- pods usually have a one-to-one relationship with containers running your application.
- To scale up, you create new pods. And to scale down, you delete existing pod.
- You do not add additional containers to an existing pod to scale your application.

### Are we restricted to having a single container? in a single pod? 
- No, A single pod can have multiple containers, except for the fact that they're usually not multiple containers of the same kind.
- For example: Sometimes you might have a scenario where you have a **helper container** that might be doing some kind of supporting task for your web application, such as processing a user and they're data processing a file uploaded by the user. and you want these **helper containers** to live alongside your application container. 
- In that case, you can have both of these containers part of the same pod
- so that when a new application container is created, the helper is also created and when it dies, the helper also dies since they're a part of the same pod.

![image](https://user-images.githubusercontent.com/87442305/209914392-a716e572-9703-4dd6-8b50-549ded76cee2.png)

# PODS with YAML
- Kubernetes uses YAML files as inputs for the creation of objects such as pods, replicas, deployments, services, et cetera.
- A Kubernetes definition file always contains four top level fields; the API version, kind, metadata, and spec. These are also required fields  
1. ```apiVersion```: This is the version of the Kubernetes API we are using to create the object.
2. ```kind```: The kind refers to the type of object we are trying to create
3. ```metadata```:The metadata is data about the object like its name, labels, etc. this is in the form of a dictionary, so everything under metadata is intended to the right a little bit and so names and labels are children of metadata.
4. ```spec```: The specification section, Depending on the object we are going to create, this is where we would provide additional information to Kubernetes pertaining to that object. 

![image](https://user-images.githubusercontent.com/87442305/209917996-a90fa7f4-7e98-4bcf-b05d-5583127e73c6.png)

### Commands:

- ```kubectl create -f <file-name>``` : To create pod in kubernetes
- ```kubectl get pods``` : to get pods
- ```kubectl describe pod <pod-name>``` : to see detailed information about the pod

# Replication Controller
- To prevent users from losing access to our application, we would like to have more than one instance or pod running at the same time.
- The Replication Controller helps us run multiple instances of a single pod in the Kubernetes cluster
- Even if you have a **_single pod_**, the Replication Controller can help by automatically bringing up a new pod when the existing one fails.
- Thus, the Replication Controller ensures that the specified number of pods are running at all times even if it's just one or 100.
- **Load Balancer and Scaling:** the Replication Controller spans across multiple nodes in the cluster. It helps us balance the load across multiple pods on different nodes as well as scale our application when demand increases

# Difference between RC and RS

| **Replication Controller** | **Replica Sets** |
|------------------------|--------------|
| Replication Controller is the older technology | Replica Set is the new recommended way to set up replication. |
| ensures a specified number of replicas of a pod are running at any given time | ensures that the correct number of pods are running and available, and if any pods fail, the ReplicaSet will create new ones to replace them. |
| more basic and do not have some of the features and functionality of ReplicaSets | Advance than replication controller feature-rich and provide better support for rolling updates and self-healing |

- ReplicationControllers may still be used in certain situations where their simpler functionality is sufficient.

### Let us now look at how we create a Replication Controller.
![image](https://user-images.githubusercontent.com/87442305/209922251-f5a72310-d7e1-491c-8ba7-0f6c1529b2c0.png)

```replicas``` : Input the number of replicas needed

### Commands for Replication Controller
- ```kubectl create –f replicaset-definition.yml ``` : to create replicaset

![image](https://user-images.githubusercontent.com/87442305/209922970-4683f4f6-4c53-45d5-ba80-9e0a61e8c83b.png)

- ```kubectl get replicaset``` : to see replication controller listed

![image](https://user-images.githubusercontent.com/87442305/209922948-f7a8a6ce-1b15-40fe-845e-a04b4c5c0a4b.png)

- ```kubectl get pods ``` : To check how many pods/replicas have been created (As we created 3 replicas in above yml file, it will create 3 pods)
 
![image](https://user-images.githubusercontent.com/87442305/209922922-900aee29-e90e-413c-b3d5-075f6f9ed320.png)

