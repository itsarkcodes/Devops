# What is ETCD?
ETCD is a distribute reliable key-value store that is simple, secure and fast

## What is key-value store?
- A key-value store stores information in the form of documents or pages. So each individual gets a document and all information about that individual is stored within that file. 
- These files can be in any format or structure and changes to one file does not affect the others. 
![image](https://user-images.githubusercontent.com/87442305/209459214-2a8e905c-a239-4ad2-aa9b-896cf54bef80.png)   ![image](https://user-images.githubusercontent.com/87442305/209459215-77e5ebba-297c-40a3-b446-6e2abf4603ad.png)

- ETCD Listens to port 2379 and the ip of the server

![image](https://user-images.githubusercontent.com/87442305/209610895-4695a8b2-fc99-4313-a47d-7d709036b831.png)

- When you run ETCD, it starts a service that listens on port 2379 by default.
- A default client that comes with ETCD is the ETCD control client. The ETCD control client is a command line client for ETCD. You can use it to store and retrieve key-value pairs.
- ```./etcdtl --version``` will give etcdctl version and api version.
- ```./etcdctl ``` will list all the supported commands

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
> kubectl get pods -n kube-system

