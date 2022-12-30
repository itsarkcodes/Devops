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
- ```kubectl delete pod <pod-name>``` : to delete a pod

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
- ```> kubectl create –f rc-definition.yml``` : to create replication controller

![image](https://user-images.githubusercontent.com/87442305/209952192-10919408-a97a-4869-8104-a8a01ecd51bb.png)

- ``` kubectl get replicationcontroller``` : to see replication controller listed

![image](https://user-images.githubusercontent.com/87442305/209952233-2b53f2be-714c-4fe9-9cbf-1bbd469f2422.png)

- ```kubectl get pods ``` : To check how many pods/replicas have been created (As we created 3 replicas in above yml file, it will create 3 pods)
 
![image](https://user-images.githubusercontent.com/87442305/209952362-afaf9929-b83f-4938-8d84-7036bc9a2ac2.png)

### Let us now look at how we create a Replica Set.

![image](https://user-images.githubusercontent.com/87442305/209951981-8a3e2a48-58c9-4cc2-9fe3-86fffb6b8a43.png)

```selector``` : The selector section helps the Replica Set identify what pods fall under it. It's because Replica Set can also manage pods that were not created as part of the Replica Set creation.

```matchLabels``` : The match labels selectors simply matches the labels specified under it to the labels on the pod.

### Commands for Replica Sets
- ```kubectl create –f replicaset-definition.yml``` : to create replicaset

![image](https://user-images.githubusercontent.com/87442305/209952399-a4d9736d-07cf-422a-9474-3a2178641e40.png)
 
- ```kubectl get replicaset``` : to see the created replicas 

![image](https://user-images.githubusercontent.com/87442305/209952507-4f736c1c-f35c-43cc-89a0-5a388dfcb341.png)

- ```kubectl get pods``` : To check how many pods/replicas have been created

![image](https://user-images.githubusercontent.com/87442305/209952573-819e8b12-66d7-4e41-ac3e-01cf10227f4a.png)

## Labels and Selectors
- There could be hundreds of other pods in the cluster running different applications.
- This is where labeling our pods during creation comes in handy.
- We could now provide these labels as a filter for Replica Set. Under the selector section, we use the match labels filter and provide the same label that we usedwhile creating the pods.

![image](https://user-images.githubusercontent.com/87442305/209967642-f8011f3b-e712-4617-9f5e-a80338e1133b.png)

## Scale
> How do we update our Replica Set to scale to six replicas?

There are multiple ways to do it.

**1st Method:**

- update the number of replicas in the definition file to six.
- Then run the kubectl replace command to specify the same file using the -F parameter ```kubectl replace -f replicaset-definition.yml```
- and that will update the Replica Set to have six replicas.

**2nd Method:**

- to run the kube control scale command, use the replicas parameter to provide the new number of replicas and specify the same file as input.

``` kubectl scale -–replicas=6 –f replicaset-definition.yml```

- You may either input the definition file or provide the Replica Set name in the type name format.

```kubectl scale -–replicas=6 replicaset myapp-replicaset```

- However, remember that using the file name as input will not result in the number of replicas being updated automatically in the file.

# Deployments

- The deployment provides us with the capability to upgrade the underlying instances seamlessly using rolling updates, undo changes, and pause, and resume changes as required.

## How to create a deployment?

- create a deployment definition file.
- The contents of the deployment definition file are exactly similar to the ReplicaSet definition file, except for the **kind** which is now going to be **deployment.**

![image](https://user-images.githubusercontent.com/87442305/209970728-7d70fe10-8759-429a-b599-7f7667fe832a.png)

- Then, run the cube control get deployment command to see the newly created deployment. The deployment automatically creates a ReplicaSet ```kubectl create –f deployment-definition.yml```

-  so if you run ```kubectl get deployments``` command, you will be able to see a new ReplicaSet in the name of the deployment.

![image](https://user-images.githubusercontent.com/87442305/209971034-8f88fe74-4c5c-4aee-a9f3-9ea3644b4e89.png)

- The ReplicaSets ultimately create pods, so if you run the ``` kubectl get pods``` command you will be able to see the pods with the name of the deployment and the ReplicaSet.

![image](https://user-images.githubusercontent.com/87442305/209971202-97f9bccd-fcb7-44ea-8a9e-af09a0f57e10.png)

## Commands:

- ```kubectl get all``` : to see all the created objects at once,

![image](https://user-images.githubusercontent.com/87442305/209971385-788edb1c-b71d-450c-8e83-231fe57500d4.png)

- we can see that the deployment was created
- and then we have the ReplicaSet followed by three parts that were created as part of the deployment.








