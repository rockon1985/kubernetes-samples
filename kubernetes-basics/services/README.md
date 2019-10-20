
Here we would explore basic three types of services offered in Kubernetes:
1. ClusterIP
2. NodePort
3. LoadBalancer

## ClusterIP Service

### Creating the service
```
kubectl apply -f cluster-ip-service.yaml
```

### View the Service
```
kubectl get service cluster-ip-service
```

the output shows a `CLUSTER-IP` field which is the cluster wide accesible IP for the service and `PORT` at which proces is running.

### Access the service
List the running the running pods
```
kubectl get pods
```

Enter into one of the running pods
```
kubectl exec -it [POD-NAME]
```

Install curl by command `apk add --no-cache curl` and check by hitting the clusterIP:
```
curl [CLUSTER_IP]:[PORT]
```


## NodePort Service

### Creating the service
```
kubectl apply -f node-port-service.yaml
```

### View the Service:
```
kubectl get service my-np-service --output yaml
```

The output shows a nodePort value


If the nodes in your cluster have external IP addresses, find the external IP address of one of your nodes:

```
kubectl get nodes --output wide
```
### Access the service

In your browser's address bar, enter `[NODE_IP_ADDRESS]:[NODE_PORT]`

where [NODE_IP_ADDRESS] is the external IP address of one of your nodes [NODE_PORT] is your node port value

## Load Balancer Service

### Creating the service

Verify that three Pods are running which were created using `deployment/simple-deployment.yaml`:
```
kubectl get pods
```

The above command should list down pods running.

Create a Load Balancer service by:
```
kubectl apply -f load-balancer-service.yaml
```

### View the Service:
```
kubectl get service node-app-lb-service --output yaml
```
The output will show a stable external IP address under `loadBalancer:ingress` field

### Access the Service
In your browser's address bar, enter `[LOAD_BALANCER_ADDRESS]:30001`

The LoadBalancer propogates the request to any of the three running pods. You can check this by opening logs of all the three pods in three new terminals:
```
kubectl logs [POD-NAME] -f
```