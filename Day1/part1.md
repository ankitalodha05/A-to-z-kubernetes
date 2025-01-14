# Step-by-Step Guide for EKS Cluster Setup and Debugging

## 1. Create an EKS Cluster Without a Node Group

Run the following command to create an EKS cluster without a node group:

```bash
eksctl create cluster --name=eksdemo1 \
  --region=us-east-1 \
  --zones=us-east-1a,us-east-1b \
  --without-nodegroup
```

## 2. Verify Cluster Creation

To confirm the cluster was successfully created, use the command:

```bash
eksctl get cluster
```

## 3. Associate IAM OIDC Provider

Enable IAM OIDC provider for the cluster with the following command:

```bash
eksctl utils associate-iam-oidc-provider \
  --region us-east-1 \
  --cluster eksdemo1 \
  --approve
```

## 4. Generate an SSH Key

Create an SSH key to use for accessing node instances. For example:

```bash
ssh-keygen -t rsa -b 2048 -f kube-demo
```

## 5. Create a Node Group

Add a managed node group to the EKS cluster:

```bash
eksctl create nodegroup --cluster=eksdemo1 \
  --region=us-east-1 \
  --name=eksdemo1-ng-public1 \
  --node-type=t3.medium \
  --nodes=2 \
  --nodes-min=2 \
  --nodes-max=4 \
  --node-volume-size=20 \
  --ssh-access \
  --ssh-public-key=kube-demo \
  --managed \
  --asg-access \
  --external-dns-access \
  --full-ecr-access \
  --appmesh-access \
  --alb-ingress-access
```

## 6. Verify Node Group

Check the created node group using:

```bash
eksctl get nodegroup --cluster=<clusterName>
```

---

## 7. Debugging and Accessing Pods

### View Pod Logs

To view the logs of a specific pod:

```bash
kubectl logs <pod-name>
```

### Access Pod Shell

To access the shell of a running pod:

```bash
kubectl exec -it <pod-name> -- /bin/bash
```

### Inspect Files Inside Pod

Once inside the pod shell, navigate to a directory and inspect files. For example:

```bash
cd /usr/share/nginx/html
cat index.html
```

---

## 8. Delete All Resources

To delete the cluster and all associated resources:

### Delete the Node Group

```bash
eksctl delete nodegroup --cluster=eksdemo1 --name=eksdemo1-ng-public1
```

### Delete the Cluster

```bash
eksctl delete cluster --name=eksdemo1 --region=us-east-1
```

### Delete the SSH Key

If required, manually delete the SSH key file:

```bash
rm kube-demo kube-demo.pub
```

---

This guide combines creating a cluster, configuring a node group, and debugging pods in Kubernetes, along with steps to clean up all resources. Let me know if you need further assistance!
