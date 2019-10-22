# Volumes

Volumes are persistent storage attached with the pod that can outlive the pod's lifecycle. We can attach a volume and based on its type it can or cannot persist the data even when the pod is destroyed or recreated.

## Types of Volumes

There are several types of volumes options available in Kubernetes. You can find a full list [on this link](https://kubernetes.io/docs/concepts/storage/volumes/#types-of-volumes). We are going to discuss few which are generally used.

### 1. Persistent Volumes Claim

A `persistentVolumeClaim` volume is used to mount a PersistentVolume into a Pod. PersistentVolumes are a way for users to “claim” durable storage (such as a GCE PersistentDisk or an iSCSI volume) without knowing the details of the particular cloud environment.

To create a pod with persistent volume you need to reserve a persistent volume claim first.
```
kubectl apply -f simple-pvc.yaml
```

Then you can create a pod that uses created PVC as persistent storage
```
kubectl apply -f using-pvc.yaml
```

### 2. emptyDir

`emptyDir` is a non persistent volume storage. It contains data as long as the pod is running on a Node. Once the pod gets destroyed, its contents gets deleted. It is ideal storage for rough work space or space to keep temporary files in your app.

### 3. ConfigMaps and Secrets

ConfigMaps and Secrets can also be used to mount files and can be used as storage. They persist the data even when the using pod is deleted as they are individual resources in kubernetes cluster.

See the folders `kubernetes-advanced/configmaps` and `kubernetes-advanced/secrets` for thier usage.