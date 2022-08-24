# Namespace
- It a virtual cluster within a cluster
- One can group resources of one type under one namespace.
- K8s give 4 default namespaces
	1. **kube-system** -> User *do not* create or modify in kube-system.
										-> It contains system processes
										-> It also contains Mater and kubectl processes.
	2. **kube-public** -> It contains publicly accessible data that do not require 
											authentication		
									   -> A configmap, ehich contains cluster information. 
									   
	 3. **kube-node-lease** -> It contains info about heartbeat of nodes.
	 											 -> Each node gets its own lease object in namespace.
												 -> Which determines its availability.
	
	 4. **default** -> In this namespace we create our resources.


###### Need for namespaces
1. It helps in overviewing our cluster in a big project. 
2. Its a way to organize our resources so that it becomes easy to access them.
3. If multiple teams are working in same cluster but different deployments then it provides safety that they dont overwrite each other. Also it can provide security by restricitnig access of each others namespaces.
4. If we are running multiple version of same app then it can be deployed in different namespaces and can still share the resources needed.
5. Limit the resources each namespace can use.

##### Charcteristics of namespace
- You cannot access most resources from another namespace like configmap and secret. You will have to create separate configmap and secret for each namespace.
- Service can be accesses from another namespaces.
- There are some components that cannot be grouped in NS. They live globally in a cluster. Example, persistant volume and node.

> To change default namespace kubectl has no solution. One has to use kubens.
