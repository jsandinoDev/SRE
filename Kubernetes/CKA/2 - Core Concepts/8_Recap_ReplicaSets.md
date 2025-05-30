# Replica Sets


### **Replication controller** 

- Helps to run multiple instances of a pod in the k8 cluster
- Even if uou have a single pod, the controller helps to bring up a new pod when the existing one fails
- Load Balancing & Scaling


Similar term

- Replication controller -> old tech replace by replicat set
- Replica set -> new tech


#### Replication Controller
rc-definition.yml
```yaml
apiVersion: v1
kind: ReplicationController
metada: 
  name: myapp-rc
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
```

```shell
kubectl create -f rc-definition.yml

kubectl get replicationcontroller

kubectl get pods
```


#### Replica Set

Monitor the pods


rc-definition.yml
```yaml
apiVersion: apps/v1
kind: ReplicaSet
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

Selector: used to add the replica set to already created pods

MatchLabels: Match the labels specified

```shell
kubectl create -f rc-definition.yml

kubectl get replicaset

kubectl get pods
```


#### Scale Replica Set

- Upate the number of replicas in the definition file
```
kubectl replace -f rc-definition.yml
```
- Use kubectl replica command
```
kubectl scale --replicas=6 -f rc-definition.yml
OR
kubectl scale --replicas=6 replicaset myapp-replicaset (name: myapp-replicaset)
```



#### Edit Replica Set

```
kubectl edit rs new-replica-set
```