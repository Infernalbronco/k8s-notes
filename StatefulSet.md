# StatefulSet
- Deployment creates/deletes/names the pods randomly as all the pods are identical.
- Whereas the stateful pods are not identical as they can have different state.
- Replica pods of stateful app is not identical.
- It gives sticky identity to each pod.
- Created from same specification but are not interchangeable.
- persistent identifier across any re-scheduling. When a pod dies and a new pod is created to replace it, the ID remains the same.
- Not all the replica pods are allowed to write to the DB. 
- The one that writes to the DB is called *Master* while others are called *Worker*.

![[statefulSet.png]]

- Master and worker pods access the same data but they use different physical storage.
- When master changes data, the worker must update thier storage or synchronize thier storage with that of the master.
- When a new pod gets added to the cluster, it replicates the data from the previous pod and then listens for changes.
-  \$(statefulset name)-\$(ordinal).
-  Next pod is created , if previous pod is up and running.
-  Each pod has its own DNS name.

![[pod_DNS.png]]
	
- \$[pod name].\$[governing service domain]
- 