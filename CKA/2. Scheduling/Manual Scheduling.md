# How Scheduling Works?
- Every POD has a field called nodeName that by default is not set. Kubernetes will create this field automatically.
- The scheduler goes through the all PODs and looks for those that don’t have this property set.
- It then identifies the right node for the POD by running the scheduling the algorithm
- it schedules the POD on the node by setting the nodeName property to the name of the node by creating the binding object.

## No Scheduler?
- If there is no scheduler to monitor and schedule a node, the pod remains in the pending state

![image](https://user-images.githubusercontent.com/87442305/210581327-4f28ca84-fe83-4185-ac3a-8c0853b9be85.png)

## How to assign PODS to node manually?
- Without a scheduler the easiest way to schedule a POD is to simply set the nodeName field to the name of the node in your POD specification file while creating the POD
- the POD then gets assigned to the specified node.

![image](https://user-images.githubusercontent.com/87442305/210581697-08841f43-fddb-4a36-af24-03d811768809.png)

![image](https://user-images.githubusercontent.com/87442305/210581802-2d58c078-e709-43a3-b5cd-9246e4ec5878.png)


- if the POD is already created and you want to assign POD to a node, Kubernetes wont allow you to do that
- another way to assign existing POD to node is to create a **binding object** and sent a **post request** to the PODs binding API. This is what the actual scheduler does.

![image](https://user-images.githubusercontent.com/87442305/210582671-98f85676-46b0-45d3-a028-5d62eef89695.png)

- In the binding object we specify the target node with a name of the node. 
- Then send a post request to the PODs binding API by setting data property in the JSON format. 
- Here you must convert your YAML to its equivalent JSON format.

```bash
curl --header "Content-Type: application/json" --request POST --data
'{
  "apiVersion": "v1",
  "kind": "Binding",
  "metadata": {
    "name": "nginx"
  },
  "target": {
    "apiVersion": "v1",
    "kind": "Node",
    "name": "node02"
  }
}' http://$SERVER/api/v1/namespaces/dafault/pods/$PODNAME/binding
```

