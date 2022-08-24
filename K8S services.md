# Services
- Types of services
	1. **Cluster IP** -> default type.
								  -> Internal service.
								  
	2.  **Headless service** -> Used when client wants to talk to pods directly.
												 -> Used when endpoints want to talk to each other.
												 -> Use case : stateful app.
												 -> Client needs to figure out IP address of each pod.
												 -> K8S allow user to find pod IP by using DNS lookup.
												 -> DNS lookup for service - return single IP address   
												 (clustrer IP).
												 -> Set ClusterIP in spec to *None* in service YAML file - returns the IP address of all the pods.
												 -> Stateful app have both ClusterIP and headless service. 
												 

