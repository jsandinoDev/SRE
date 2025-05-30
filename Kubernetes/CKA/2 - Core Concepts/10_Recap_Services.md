# Services

Enable connectivity between pods and external data source


Types

- Node port:  Object that listen to requests and forwards 
- ClusterIP: Create a virutal IP inside the cluster to enable communitcation
- LoadBalancer


### Node Port

- NodePort: port of the node
- Port: port of the service
- TargetPort: port of the pod



Has a range from 30000 - 23767

service-definition.yml
```yaml
apiVersion: v1
kind: Service
metada: 
    name: myapp-service
  
spec:
    type: NodePort
    ports:
      - targetPort: 80
        port: 80
        nodePort: 30008
    selector:
        app: myapp
        type: frontend
```

```shell
kubectl apply -f service-definition.yml

kubectl get services

kubectl get all
```

For many pods, they should have the same label to be connected to the service

For many nodes, k8 automatically create a service to connect nodes


---

### Cluster IP

Allow to group the pods together in a group to be accesible

Example 
1 service for backend pods
1 service for front
1 service for DB

service-definition.yml
```yaml
apiVersion: v1
kind: Service
metada: 
    name: BackEnd
  
spec:
    type: ClusterIP
    ports:
      - targetPort: 80 #where the backend is exposed
        port: 80
    selector:
        app: myapp
        type: frontend
```

```shell
kubectl apply -f service-definition.yml

kubectl get services

kubectl get all
```

---

### Load Balancer
Only work with supported cloud platforms

service-definition.yml
```yaml
apiVersion: v1
kind: Service
metada: 
    name: BackEnd
spec:
    type: LoadBalancer
    ports:
      - targetPort: 80 
        port: 80
        nodePort: 30008

    selector:
        app: myapp
        type: frontend
```

```shell
kubectl apply -f service-definition.yml

kubectl get services

kubectl get all
```
