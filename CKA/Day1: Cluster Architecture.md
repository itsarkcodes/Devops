# Kubernetes Architecture
![image](https://user-images.githubusercontent.com/87442305/209455628-6120ee64-68f6-49f6-bfc4-7d3d28488d8a.png)

The purpose of Kubernetes is to host your applications in the form of containers in an automated fashion so that you can easily deploy as many instances of your application as required and easily enable communication between different services within your application

To understand Kubernetes, we will take analogy of a Ship as examples

![image](https://user-images.githubusercontent.com/87442305/209457716-abf4d390-63ec-4843-ae7a-8d2fdccf7ebf.png)
 
 ### Worker Node 
 - The worker nodes in a cluster are the machines or physical servers that run your applications
 
 ### Master Node:
 - The worker nodes in a cluster are the machines or physical servers that run your applications
 
 ## Master Node components 
 1. ETCD: It is a distributed key-value store that is used to store the cluster state. Kubernetes stores the file in a database called the etcd
 
 ```Eg: To maintain information about the different ships, what container is on which ship and what time it was loaded, etc```
 
 2. Kube-scheduler: Kube-scheduler is used to schedule the work to different worker nodes. It also manages the new requests coming from the API Server and assigns them to healthy nodes.

```Eg:When ships arrive, you load containers on them using cranes. The cranes identify the containers that need to be placed on ships. It identifies the right ship based on its size, its capacity, the number of containers already on the ship and any other conditions such as the destination of the ship, the type of containers it is allowed to carry, etc```

3. Controller Manager: 
There are different types of control manager in Kubernetes architecture:

- Node Manager: it manages the nodes. It creates new nodes if any node is unavailable or destroyed.
- Replication Controller: it manages if the desired number of containers is running all time in the replication group.
- Endpoints controller: it populates the endpoints object that is, joins Services & Pods.

``` 
A example for Contoller manager can be

There are different offices in the dock that are assigned to special tasks or departments. 
The operations team takes care of ship handling, traffic control. 
The cargo team takes care of containers. When containers are damaged or destroyed,they make sure new containers are made available.
We have these services office that takes care of the IT and communications between different ships.
```

4. Kube API-server: The Kube API server is a key component of Kubernetes that manages and coordinates all operations within a cluster. It provides an API for external users to manage the cluster, as well as for controllers to monitor the cluster and make changes as needed, and for worker nodes to communicate with the server. Essentially, it is the "brain" of the cluster that controls and oversees everything that happens within it


## We have to make everything container compatible as we are working with containers and they are everywhere

We need softwares that run containers

So we need Docker, or it's supported equivalent installed on all the nodes in the cluster, including the master nodes, if you wish to host the controlling components as containers.

Kubernetes supports other runtime engines as well like ContainerD, a Rocket.

 ## Worker Node Components
 
 1. Kubelet: It is an agent that runs on each worker node and communicates with the master node. It also makes sure that the containers which are part of the pods are always healthy. It watches for tasks sent from the API Server, executes the task like deploy or destroy the container, and then reports back to the Master.

``` Eg: The captain on the ship. The captain is responsible for managing all activities on these ships. The captain is responsible for cooperating with the master ships, starting with letting the mastership know that they're interested in joining the group, receiving information about the containers to be loaded on the ship and loading the appropriate containers as required```

2. Kube-proxy: It is used to communicate between the multiple worker nodes. It maintains network rules on nodes and also make sure there are necessary rules define on the worker node so the container can communicate to each in different nodes.

```Eg: You might have a web server running in a container on one of the nodes and a database server running on another container on another node. How would the web server reach the database server on the other node? Communication between worker nodes are enabled by another component that runs on the worker node known as the Kube Proxy Service. ```

## Reference
https://k21academy.com/docker-kubernetes/kubernetes-architecture-components-overview-for-beginners/ 
