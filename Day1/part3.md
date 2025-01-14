# ReplicaSet Operations: A Comprehensive Guide

## 1. Create a ReplicaSet
```bash
kubectl create -f reploca-dem.yml
```

## 2. View ReplicaSet and Pods
```bash
kubectl get replicaset
kubectl get rs
kubectl describe rs my-helloworld-rs
kubectl get pods -o wide
kubectl describe pod my-helloworld-rs-<pod_suffix>
```

## 3. Retrieve Pod Details
```bash
kubectl get pods my-helloworld-rs-<pod_suffix> -o yaml
```

## 4. Namespace Management
```bash
kubectl create namespace kavitha
kubectl get ns
```

## 5. Expose ReplicaSet as a Service
```bash
kubectl expose rs my-helloworld-rs --type=NodePort --port=80 --target-port=8080 --name=my-np-svc
kubectl get svc
```

## 6. View Logs
```bash
kubectl logs my-helloworld-rs-<pod_suffix>
```

## 7. Delete Pods, ReplicaSet, and Service
```bash
kubectl delete pod my-helloworld-rs-<pod_suffix>
kubectl delete rs my-helloworld-rs
kubectl delete svc my-np-svc
```

## Additional Useful Commands

### General Information
```bash
kubectl get nodes -o wide
kubectl options
```

### Updating ReplicaSet
```bash
kubectl replace -f reploca-dem.yml
