# Kubernetes Deployment Guide

This document provides a step-by-step guide to deploying an application in Kubernetes using `kubectl` commands.

---

## 1. Create a Deployment

Use the following command to create a deployment with a specified container image:

```bash
kubectl create deployment my-first-deployment --image=stacksimplify/kubenginx:1.0.0
```

## 2. Verify the Deployment

Check the deployments created:

```bash
kubectl get deployment
```

Verify all resources, including pods:

```bash
kubectl get all
```

Get detailed information about the deployment:

```bash
kubectl describe deployment my-first-deployment
```

## 3. Manage Replica Sets and Pods

Check the current replica sets:

```bash
kubectl get rs
```

Check the current pods:

```bash
kubectl get po
```

Scale the deployment to 20 replicas:

```bash
kubectl scale --replicas=20 deployment/my-first-deployment
```

Verify the deployment after scaling:

```bash
kubectl get deploy
```



Check the updated replica sets:

```bash
kubectl get rs
```

Check the updated pods:

```bash
kubectl get po
```

For detailed pod information, including node assignments:

```bash
kubectl get po -o wide
```

## 4. Expose the Deployment

Expose the deployment as a service of type `NodePort`:

```bash
kubectl expose deployment my-first-deployment --type=NodePort --port=80 --target-port=80 --name=my-first-deployment-service
```

Verify the services:

```bash
kubectl get svc
```

## 5. Check Node Information

Get detailed information about the nodes, including internal and external IP addresses:

```bash
kubectl get nodes -o wide
```

## 6. Rollout and Deployment Status

Check the rollout status of the deployment:

```bash
kubectl rollout status deployment my-first-deployment
```

Describe the deployment for detailed status:

```bash
kubectl describe deployment my-first-deployment
```

## 7. Rollout History and Editing

Check the rollout history of the deployment:

```bash
kubectl rollout history deployment/my-first-deployment
```

Edit the deployment (for example, to update the image):

```bash
kubectl edit deployment/my-first-deployment --record=true
```

Verify the updated rollout status:

```bash
kubectl rollout status deployment/my-first-deployment
```

Check the updated rollout history:

```bash
kubectl rollout history deployment/my-first-deployment
```

## 8. Verify Pods After Update

Check the pods to ensure they are running correctly after the update:

```bash
kubectl get po
```

---

## Summary

In this guide, we created a deployment, scaled it to multiple replicas, exposed it as a NodePort service, and verified the deployment, services, and nodes. Additionally, we reviewed rollout history, edited the deployment, and verified the updated pods. This workflow demonstrates the basic and advanced steps to deploy and manage applications in Kubernetes.

