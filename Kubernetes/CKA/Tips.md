# Certification TIPS

Edit

```SHELL
kubectl edit deployment blue
```    

View Events

```SHELL
kubectl get evetns -o wide
```  

To create or edit yml files use the **RUN** command
```SHELL
kubectl run nginx --image=nginx

# Generate POD manifest YAML file
kubectl run nginx --image=nginx --dry-run=client -o yaml

kubectl run nginx --image=nginx --labels="tier=db"


# Create Deployment
kubectl create deployment --image=ngin nginx

kubectl create deployment webapp --image=nginx -r=3

kubectl expose deployment nginx --port 80

# Set Node Affinity to the deployment

# Service
kubectl expose pod redis --port=6379 --name redis-service


# POD & SERVICE
kubectl run httpd --image=httpd:alpine --port=80 --expose

```



Update Object
```SHELL
kubectl edit deployment nginx
kubectl scale deployment nginx --replicas=5
kubectl set image deployment nginx nginx=nginx:1.18
```

Running
- ```--dry-run``` = will create the resource
- ```--dry-run=client``` = will not create, just tell if the command is ok
- ```-o yaml``` = will output the resource definition in a yaml format 