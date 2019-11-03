# Nodejs App Kubernetes Setup

## Procedure

### 1. Create the deployment

The deployments would create the intended pods running rails and sidekiq services. If you don't wish to start sidekiq, comment out the sidekiq deplloyment part. You can also update the number of app replicas that should be running. Once the desired updates are done, fire the command below to spin up the pods

```
kubectl apply -f app-deployments.yaml
```

### 2. Expose the app using services

Once your app is running, in order to access it from outside the cluster you need to expose it using services. Here you can go with one of the two options:
- `LoadBalancer` service: change the `type` to LoadBalancer and add a nodePort to which the app would be exposed.

```
kubectl apply -f service.yaml
```

- `Ingress`: Exposing the app using Ingress exposes it globally rather than region. It also gives an option to assign a static IP address to the app, which is a must for production grade applications. In order to use ingress, the `type` field in app-service.yaml must be set to `NodePort`.
**Note** before applying `ingress.yaml` file you need to also apply `service.yaml` file

```
kubectl apply -f ingress.yaml
```
