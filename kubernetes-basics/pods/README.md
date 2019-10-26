A pod is the smallest manageable entity by kubernetes. A pod may run one or multiple container in itself.

Although as a common practice, we usually run only single container in one pod. A pod is the entity that runs our application in a docker container.

## Creating a Pod

To create a single pod you can write a resource of `kind: Pod` in a yaml file.

```
kubectl apply -f simple-pod.yaml
```

## Managing Pods

Creating a pod directly this way is very rare in kujbernetes. The reason is that **Pods are not self healing**. If one pod gets crashed, it does not get recreated automatically. That's why we use `Deployments` or `StatefulSets` to manage the lifecycle and required state of pods.

## Pods with multiple containers:

There are few cases where we might want to run multiple containers in a single pod. The primary reason that Pods can have multiple containers is to support helper applications that assist a primary application.

```
kubectl apply -f pod-with-multiple-containers.yaml
```