# Volumes
##### Persistant Volume
- A global cluster resource.
- Created via YAML file
	- kind: Persistant Volume
	- spec e.g. how much storage?
- Its an external plugin to the cluster.

![[NFS_storage.png]]

- Persistant volumes are not namespaced.

##### Persistant volume claims
- Created using YAML file.
- It claims the volume that satisfies the storage requirement and properties.
- If there are many persistant volumes with different sizes then it will claim that PV with minimum storage that satisfies the claim.

```mermaid
flowchart LR

id1([pod requests volume through the PVC]) ==> id2([Claim tries to find the volume in the cluster]) ==> id3([volume has the actual storage backend])

```

- Claims must exist in the same namespace as the pod that is using it.

```
apiVersion:v1
kind:Pod
metadata:
  name:mypod
spec:
  containers:
      name:myfrontend
      image:nginx
      volumeMounts:
      -mountPath:"/var/www/html"
        name:mypd
      name:mypd
      persistentVolumeClaim:
        claimName:pvc-name
  volumes:
```

```mermaid
flowchart LR

id1([volume is mounted into the pod]) ==> id2([Volume is then mounted in the containers])
```

- Admin creates PV.
- User creates PVCs.

### Storage Class
- SC provisions PV **dynamically** when PVC claims it.
- We dont need to create a PV before deploying a pod.
- We can create a StorageClass config with the Storagebackend that is to be used to create PVs. It is defined using the attribute provisioner.
- In the PVC of the pod itself, we can link the StorageClass config file.
- Then the StorageClass will create s PV that will satisfiy the claims of PVC.

```mermaid
flowchart LR

id1([Pod claims storage via PVC]) ==> id2([PVC requests storage from SC]) ==> id3([SC creates PV that meets the needs of the claim])

```

```mermaid
flowchart TB

id1(pod) == requests ==> id2(pvc) == requests ==> id3(SC) == creates ==> id4(pv)

id2 == uses ==> id4

```