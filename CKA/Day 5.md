# Services
- Kubernetes Services enable communication between various components within and outside of the application.
- Kubernetes Services helps us connect applications together with other applications or users

![image](https://user-images.githubusercontent.com/87442305/210403253-01800fc8-a71e-4588-9f1c-29d2e20f864f.png)

## Service Types:

### 1. NodePort:
- NodePort where the service makes an internal port accessible on a port on the node.
- This service can help us by mapping a port on the node to a port on the Pod.
- yaml file for nodeport service:

![image](https://user-images.githubusercontent.com/87442305/210406420-dc0ee3a1-d2e8-401b-a1d5-8bfd54991496.png)

- the only mandatory field is **port**.
- If you don't provide a targetPort, it is assumed to be the same as port.
- To connect the service to the pod we use labels and selectors of that pod

There are many disadvantages to this method.

- You can only have one service per port
- You can only use ports 30000–32767
- If your Node/VM IP address change, you need to deal with that

### 2. Cluster IP: 
- Each service gets an IP, a name assigned to it inside the cluster and that is the name that should be use by other PODs to access the service. This type of service is known as ClusterIP service.
- The YAML for a NodePort service looks like this

![image](https://user-images.githubusercontent.com/87442305/210409929-16b50a4d-90ba-49e7-b7af-c9bad7cf0a41.png)

### 3. Load Balancer:

- A LoadBalancer service is the standard way to expose a service to the internet.
- This service provisions a load balancer for your application in support to cloud providers
- The external load balancer routes to your NodePort and ClusterIP services, which are created automatically.

# Namespace
- Kubernetes creates a set of PODs, Services, Deployments for its internal purpose such as those required by the network solution, the DNS service etc. To isolate these from the user and prevent you from accidently deleting or modifying the services, Kubernetes create them under another Namespace when the cluster startup named with Kube-system.
- You can also assigns limits of resources to each of these Namespaces. That way each Namespace is guaranteed that a certain amount of resources and doesn’t use more than its allowed limit.

### Commands
``` kubectl get pods --namespace=kube-system``` : To list PODs in the another Namespace

``` kubectl get namespace --no-headers | wc -l``` : To get no. of namespace 

```kubectl create -f pod-definition.yml --namespace=dev``` : To create POD in the another Namespace you need to run following command
OR

You can also mention namespace in pod definition file under metadata section

![image](https://user-images.githubusercontent.com/87442305/210417269-422d301f-16dd-41f6-a145-6c009cdf59de.png)

### Create Namespace
![image](https://user-images.githubusercontent.com/87442305/210417431-9f877afa-c1d2-416a-a72f-f68c4cd2f77f.png)

```kubectl create –f namespace-dev.yml```: To create namespace using file 

OR

``` kubectl create namespace dev```

``` kubectl get pods --all-namespaces```: TO view all pods from all namespace

