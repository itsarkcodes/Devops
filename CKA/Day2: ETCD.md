# What is ETCD?
ETCD is a distribute reliable key-value store that is simple, secure and fast

## What is key-value store?
- A key-value store stores information in the form of documents or pages. So each individual gets a document and all information about that individual is stored within that file. 
- These files can be in any format or structure and changes to one file does not affect the others. 
![image](https://user-images.githubusercontent.com/87442305/209459214-2a8e905c-a239-4ad2-aa9b-896cf54bef80.png)   ![image](https://user-images.githubusercontent.com/87442305/209459215-77e5ebba-297c-40a3-b446-6e2abf4603ad.png)

- The etcd data store stores information regarding the cluster such as the notes, pods, convicts, secrets, accounts, roles, role bindings, and others.
- ETCD Listens to port 2379 (default) and the ip of the server

![image](https://user-images.githubusercontent.com/87442305/209610895-4695a8b2-fc99-4313-a47d-7d709036b831.png)

- When you run ETCD, it starts a service that listens on port 2379 by default.
- A default client that comes with ETCD is the ETCD control client. The ETCD control client is a command line client for ETCD. You can use it to store and retrieve key-value pairs.
- ```./etcdtl --version``` will give etcdctl version and api version.
- ```./etcdctl ``` will list all the supported commands (In API v3)
- To set a value use ``` ./etcdctl put <key1> <value1>```
- TO get a value use ```./etcdctl get key1```

## Commands in Version 2:

etcdctl backup

etcdctl cluster-health

etcdctl mk

etcdctl mkdir

etcdctl set

## Commands in Version 3:
etcdctl snapshot save 

etcdctl endpoint health

etcdctl get

etcdctl put

## Set API Version

To set the right version of API set the environment variable ETCDCTL_API command

``` export ETCDCTL_API = 3 ```

When API version is not set, it is assumed to be set to version 2. And version 3 commands listed above don't work. When API version is set to version 3, version 2 commands listed above don't work.

## Two ways to deploy 
1. From Scratch (Manual)
2. Using kubeadm tool

# Setup - Manual
1. Download Binaries
```bash
wget -q --https-only "https://github.com/coreos/etcd/releases/download/v3.3.9/etcd-v3.3.9-linux-amd64.tar.gz"
```

2. Extract the binaries
```bash
tar xzvf etcd-v3.3.11-linux-amd64.tar.gz
```

3. Run ETCD Service
```bash
./etcd
```

# Setup - Kubeadm
- If you set up your cluster using kubeadm, then kubeadm deploys the etcd server for you as a pod in the kube system namespace.

``` kubectl get pods -n kube-system ```

-To list all keys stored by Kubernetes, run the etcd control get command like this. 

``` etcdctl get / --prefix -keys-only ```

- Kubernetes stores data in the specific directory structure. 
- The root directory is a registry, and under that, you have the various Kubernetes constructs, such as minions or nodes, pods, replica sets, deployments,

![image](https://user-images.githubusercontent.com/87442305/209763311-06195d27-716e-4687-a4fb-0a0cb3e56e3d.png)


# Kube-API Server 
- The kube-apiserver is the primary management component in Kubernetes.
- When you run a kubectl command, the kubectl utility is in fact reaching to the kube-apiserver.
- In case of creation of a pod, the kube-apiserver first authenticates the request and validates it.
- The API server creates a pod object without assigning it to a node.
- Updates the information in the etcd server, updates the user that the pod has been created.
- The scheduler continuously monitors the API server and realizes that there is a new pod with no node assigned.
- The scheduler identifies the right node to place the new pod on and communicates that back to the kube-apiserver.
- The API server then updates the information in the etcd cluster.
- The API server then passes that information to the kubelet in the appropriate worker node.
- The kubelet then creates the pod on the node and instructs the container runtime engine to deploy the application image.
- Once done, the kubelet updates the status back to the API server and the API server then updates the data back in the etcd cluster.

## Summarize Kube-API Server:
- the kube-apiserver is responsible for authenticating and validating requests, retrieving and updating data in the etcd data store.
![image](https://user-images.githubusercontent.com/87442305/209765058-046b3ac1-a29f-4f16-a582-6ccd86c02a17.png)

## View api-server in a existing cluster 
- If you set it up with a kubeadmin tool, the kubeadmin deploys the kubeadmin-apiserver as a pod in the kube-system namespace on the master node.
![image](https://user-images.githubusercontent.com/87442305/209765499-6197f399-df9b-428d-8962-87b09464a63e.png)

- You can see the options within the pod definition file, located at ``` cat etc/kubernetes/manifest folder ``` .
- In a non-kubeadmin setup, you can inspect the options by viewing the kube-apiserver service located at

``` cat etc/systemd/system/kube-apiserver.service ```
