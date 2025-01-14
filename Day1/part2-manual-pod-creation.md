# Manual Pod Creation: Essential Commands and Operations

## 1. Create a Pod
```bash
kubectl run nginx-pod --image=nginx:latest --restart=Never
```

## 2. Check Pod Status
```bash
kubectl get po
kubectl get po -o wide
kubectl describe po nginx-pod
```

## 3. Namespace Operations
```bash
kubectl get ns
kubectl describe ns default
```

## 4. Expose Pod as a Service
```bash
kubectl expose po nginx-pod --type=NodePort --port=80 --name=nginx-sv
kubectl get svc
```

## 5. View Logs
```bash
kubectl logs nginx-pod
kubectl logs -f nginx-pod
```

## 6. Execute Commands Inside Pod
```bash
kubectl exec -it nginx-pod -- /bin/bash
kubectl exec -it nginx-pod env
kubectl exec -it nginx-pod cat /usr/share/nginx/html/index.html
```

## 7. Retrieve Pod Details
```bash
kubectl get pod nginx-pod -o yaml
kubectl get all
kubectl get all -o wide
```

## 8. Delete Resources
```bash
kubectl delete svc nginx-sv
kubectl delete po nginx-pod
```
