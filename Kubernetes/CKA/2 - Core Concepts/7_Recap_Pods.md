# PODS

Single instance of an app

Smallest object that you can create in k8

Usually have a 1:1 relationship


```
# Create a node/pod
kubectl run nginx --image nginx

# Get pods 
kubectlget pods
```

Creating a pod with yaml

```YAML
#pod-definition.yml
apiVersion: v1
kind: Pod
metadata: 
  name: myapp-pod
  labels: 
    app: myapp
    tier: front-end
spec:
  containers:
  - name: nginx
    image: nginx
```

```SHELL
kubectl create -f pod-definition.yml

kubectl get pods

kubectl describe pod myapp-pod

# Search in which node it is
kubectl describe pod myapp-pod | grep Node

# Generate yml file
kubectl run redis --image=redis --dry-run=client -o yaml > redis.yaml
```


