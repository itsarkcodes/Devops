# Kube Control Manager
A controller is a process that continuously monitors the state of various components within the system and works towards bringing the whole system to the desired functioning state.	

## 1. Node Controller
- The node controller is responsible for monitoring the status of the nodes and taking necessary actions to keep the applications running.
- It does that through the Kube API server.
- The node controller tests the status of the nodes every five seconds. That way the node controller can monitor the health of the nodes.
- If it stops receiving heartbeat from a node the node is marked as unreachable but it **waits for 40 seconds before marking it unreachable**.
- After a node is marked unreachable it gives it **five minutes to come back up**. 
- If it doesn't, it removes the PODs assigned to that node and provisions them on the healthy ones if the PODs are part of a replica set.

![image](https://user-images.githubusercontent.com/87442305/209831497-f1f536bb-2265-4d4d-a4df-530f99ff1cc5.png)

## 2. Replication Controller
- It is responsible for monitoring the status of replica sets and ensuring that the desired number of PODs are available at all times within the set.
- If a POD dies, it creates another one.

## Installing Kube-controller-manager
- Download the Kube controller manager from the Kubernetes release page, extract it and run it as a service.
- There is an additional option called controllers that you can use to specify which controllers to enable. 
- By default, all of them are enabled

## View kube-controller-manager 
- If you set it up with the Kube admin tool, Kube admin deploys the Kube controller manager as a POD in the Kube system namespace on the master node. 👇

![image](https://user-images.githubusercontent.com/87442305/209832653-eb0af1b2-d1d6-4e8d-bbda-09185898d3bb.png)

## To view kube-controller-manager options (using kubeadm tool)
- You can see the options

within the POD definition file located at ```cat /etc/kubernetes/manifests/kube-controller-manager.yaml```

![image](https://user-images.githubusercontent.com/87442305/209833072-31eee079-52c5-4170-8a3b-29975c4cd692.png)

## To view kube-controller-manager options (using non kubeadm tool)
- By viewing the Kube Controller Managers service located at the services directory 

``` cat /etc/systemd/system/kube-controller-manager.service ```

![image](https://user-images.githubusercontent.com/87442305/209833446-75576391-d6ee-4948-8134-47a90d9f4700.png)

# Kube Schedular
- the scheduler is only responsible for deciding which pod goes on which node. It doesn't actually place the pod on the nodes. That's the job of the kubelet. ⭐⭐

## Criteria for placing the pods, it has 2 Phases
1. Filter Nodes: 
-  the scheduler tries to filter out the nodes that do not fit the profile for this pod.
-  For example, the nodes that do not have sufficient CPU and memory resources requested by the pod.

2. Rank the Nodes: 
- The scheduler ranks the nodes to identify the best fit for the pod. 
- It uses a priority function to assign a score to the nodes on a scale of zero to 10.
- For example, the scheduler calculates the amount of resources that would be free on the nodes after placing the pod on them. The more the resources available after placing the pod, the higher the rank of that node.

# Kubelet
- The kubelet in the Kubernetes worker node registers the node with a Kubernetes cluster.
- When it receives instructions to load a container or a pod on the node, it requests the container runtime engine, which may be Docker, to pull the required image and run an instance.
- The kubelet then continues to monitor the state of the pod and containers in it and reports to the kube API server on a timely basis.

 ![image](https://user-images.githubusercontent.com/87442305/209835893-4f355a0b-2f6d-4624-9bab-2e6aa11bac26.png)
 
 ### ⭐ IMP ⭐
 - If you use the kubeadm tool to install deploy your cluster, **it does not automatically deploy the kubelet.**
 - If you use the kubeadm tool to deploy your cluster, it does not automatically deploy the kubelet.
 - Download the installer, extract it, and run it as a service.
