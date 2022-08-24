# Command List
1. **get nodes** -> Gets the status of all the nodes.
2. **get pods** -> Get the status of all the pods running.
3. **get services** -> Gets the status of all the services running.
4. **create** -> Helps you create differnt things. You can list those things using *\-h*.
	 	
		`kubectl create deployment NAME --image=image [--dry-run] [options]`
		
5.  **get deployment** -> Gets the status of all the deployments created.


 > Pod name is made up of *deployment name* + *repilcaset id* + *pod id*.
 
 6. **delete** -> To delete a pod or a replicaset or deployment, delete the deployment.
 	
	`kubectl delete deployment [deployment name]`
	
7. **apply** -> If you want to create a deployment from a configuration file, use *apply* command
	
	`kubectl apply -f [file name]`

[[yaml config file]]

### Debugging Commands


8. **logs** -> It tells what the application running iside the pod logged
	
	`kubectl logs [pod name]`

9. **describe pod** -> It tells all the state changes happening inside the pod.
10. **exec** -> It will get me the terminal of the conatainer running in the pod.
	
	`kubectl exec -it [po name] -- /bin/bash`
	