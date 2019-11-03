# kubernetes-samples
Examples covering various components of Kubernetes and their implementations

Table of Contents
====================

  * [Dockerize Your App](#dockerizing-your-app)
  * [Kubernetes Basics](#kubernetes-basics)
    * [Pods](#pods)
    * [Simple Deployment](#a-simple-deployment)
    * [Services](#services)
    * [Volumes](#volumes)
  * [Kubernetes Advanced](#command-line-interface)
    * [Secrets](#secrets)
    * [ConfigMaps](#configmaps)
    * [Jobs](#jobs)
  * [Kubernetes Examples](#kubernetes-examples)
    * [Rails App on Kubernetes](#rails-app-on-kubernetes)
    * [Node App on Kubernetes](#nodejs-app-on-kubernetes)
  * [Helm Charts](#helm-charts-examples)
    * [Intro to Helm Chart](#intro-to-helm-chart)
    * [Initializing Helm](#initializing-helm)
    * [Rails App Helm Chart](#rails-app-helm-chart) 
    * [Node App Helm Chart](#node-app-helm-chart) 

## Dockerizing your app:

In order to use Kubernetes as a container orchestrator you need to first have a docker Image to use. Although there are plenty pre built images available on dockerhub, it's always better to learn to dockerize your own app. You can find the link in the folder `node-dockerized`

## Kubernetes Basics

### Pods
A `pod` is a group of one or more containers (such as Docker containers), with shared storage/network, and a specification for how to run the containers.

### A Simple Deployment

A deployment is a way of passing kubernetes the "required state" of our cluster.

### Services

A service is used to communicate the process running within a Pod. Based on its type, a service can expose a process runnning on a Pod's port within the cluster or outside the cluster.

There are 3 types of services offered by Kubernetes

- ClusterIP: Exposes the service on a cluster-internal IP. Choosing this value makes the service only reachable from within the cluster. This is the default ServiceType.

- NodePort: Exposes the service on each Node’s IP at a static port (the NodePort). A ClusterIP service, to which the NodePort service will route, is automatically created. You’ll be able to contact the NodePort service, from outside the cluster, by requesting <NodeIP>:<NodePort>.

- LoadBalancer: Exposes the service externally using a cloud provider’s load balancer. NodePort and ClusterIP services, to which the external load balancer will route, are automatically created.

You can find the samples in `kubernetes-basics/services` folder

### Volumes

Volumes are persistent storage attached with the pod that can outlive the pod's lifecycle. 
You can find a full list of volumes available [on this link](https://kubernetes.io/docs/concepts/storage/volumes/#types-of-volumes).

The samples related to few popular types of volumes can be found in `kubernetes-basics/volumes` folder

## Kubernetes Advanced

### Secrets
Objects of type secret are intended to hold sensitive information, such as passwords, OAuth tokens, and ssh keys. You can find the examples in `kubernetes-advanced/secrets` folder.

### ConfigMaps
ConfigMaps are used to store configuration params and data needed in the pods. They allow you to decouple configuration artifacts from image content to keep containerized applications portable.

You can find the examples in ``kubernetes-advanced/configmaps` folder

### Jobs

Cron jobs are useful for creating periodic and recurring tasks, like running backups or sending emails.

## Kubernetes Examples

This section covers various examples to dockerise your applications using various components. You can find the kubernetes yaml files in the `kubernetes-examples` folder. 

### Rails app on Kubernetes

Please check the procedure and the related files in `kubernetes-examples/rails-on-kubernetes` folder.

### Nodejs app on Kubernetes

Please check the procedure and the related files in `kubernetes-examples/rails-on-kubernetes` folder.

## Helm Chart Examples

### Intro to Helm Charts
[Helm](#https://docs.helm.sh/using_helm/) is a deployment release manager on top of kubernetes. It keeps track of all the releases and provides us the option to rollback to any previous release without the efforts to update the yaml files.

Helm uses a packaging format called [helm-charts](https://docs.helm.sh/developing_charts/#charts). A chart is a collection of files that describe a related set of Kubernetes resources.

Helm charts gives us many programming constructs like `if-else`, `looping over array and objects` and helper methods to simplify our kubernetes object declaration.

### Initializing Helm

In order to use helm, you need to first install and initialize helm and tiller in your system.

**Installation** You can find the installation instruction in [this link](https://docs.helm.sh/using_helm/#installing-helm)

**Initializing**
In order to initialize helm in cluster of different providers like GCE, minikube, etc., checkout the [Helm Distribution guide](https://docs.helm.sh/using_helm/#kubernetes-distribution-guide)

### Hello world Helm chart
You can find a simple hello world Helm chart in `helm-examples/hello-world`

To run the helm chart and create kubernetes resources, use command:
```
helm install --name RELEASE_NAME ./helm-examples/hello-world-helm-chart
```

To just see the computed yaml and debugging the code, use command:
```
helm install --debug --dry-run ./helm-examples/hello-world-helm-chart
```

### Rails App Helm Chart

Please check the procedure and the related files in `helm-examples/rails-app-helm-chart` folder.
To run the helm chart and create kubernetes resources, use command:
```
helm install --name RELEASE_NAME ./helm-examples/rails-app-helm-chart
```

### Node App Helm Chart

Please check the procedure and the related files in `helm-examples/nodejs-app-helm-chart` folder.

To run the helm chart and create kubernetes resources, use command:
```
helm install --name RELEASE_NAME ./helm-examples/nodejs-app-helm-chart
```