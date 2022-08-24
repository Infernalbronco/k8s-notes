# Worker Node
- Each node has multiple pods running.
- Each node should have three processes
	1. **Container runtime**
	2. **Kubelet** -> It interacts with both the cotainer and pods. It starts the pod with container inside. It starts, schedules and stops the pods.
	3. **Kube proxy** -> It forwards the request to pods from service.
- Worker nodes do all the work.

# Master Node
- Scheduling a pod, monitoring the state of the pods, restarting a pod and when a new server joins the cluster how it becomes a node all this is managed by **Master Node**
- Each master node should have 4 processes
	1.  **API server** -> It is the gateway to the cluster. Clients interact with it to start/update a pod or query the health of the cluster. It also takes care of authentication.
	2. **Scheduler** -> When the client requests the API server to start/schedule a pod, that request is forwarded to the scheduler. Scheduler is a smart process. It takes into account the available resources on all the nodes and selects the best node for the pod. It only schedules the pod that is selects the node on which the pod will be run then forwards the request to kubelet of that node.
	3. **Controller manager** -> It detects state changes of a cluster like a pod dieing. Then requests the scheduler to schedule the pod.
	4. **etcd** -> It is the brain of the cluster. It stores all the info about the changes taking place in the cluster like the time of starting a pod or time of death of a pod. It is a key-value pair. On the basis of the data, the scheduler and controller manager makes decision. 