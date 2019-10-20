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



## Kubernetes Advanced

### Secrets
Objects of type secret are intended to hold sensitive information, such as passwords, OAuth tokens, and ssh keys. You can find the examples in `kubernetes-advanced/secrets` folder.

### ConfigMaps

### Jobs
