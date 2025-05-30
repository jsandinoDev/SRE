# Deployment

rc-definition.yml
```yaml
apiVersion: apps/v1
kind: Deployment
metada: 
  name: myapp-replicaset
  labels: 
    app: myapp
    type: front-end
spec:
    template:

       metada: 
        name: myapp-pod
        labels: 
            app: myapp
            tier: front-end
        spec:
            containers:
            - name: nginx
              image: nginx     
replicas: 3
selector: 
    matchLabels: front-end
```


```shell
kubectl apply -f rc-definition.yml

kubectl get deployment

# Deployments create a replica set
kubectl get replicaset

kubectl get all
```

Very similar to replica set with the difference of the K8 object that is created