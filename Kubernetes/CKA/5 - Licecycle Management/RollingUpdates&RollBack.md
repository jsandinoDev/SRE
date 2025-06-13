# RollingUpdates&RollBack

Check rollout 

```YAML
kubectl rollout status deployment/myapp-deployment


kubectl rollout history deployment/myapp-deployment
```

### Deploymeny Strategy

- Recreate (not used): delete pods and create new pods with new update
- Rolling Update (default): destroy and create 1 by 1

```YAML
# Can do this
kubectl set image deployment/my-app-deployment \ nginx-container=nginx:1.9.1
```


Undo a deploymeny update
```YAML
kubectl rollout undo deployment/my-app-deployment 
```


#### Summarize of commands
```YAML
# Create Deploymenyt
kubectl apply -f deployment-def.yaml

# Get 
kubectl get deployments

# Update
kubectl apply -f deployment-def.yaml
kubectl set image deployment/my-app-deployment \ nginx-container=nginx:1.9.1

#Check
kubectl rollout status deployment/myapp-deployment
kubectl rollout history deployment/myapp-deployment

# Rollback
kubectl rollout undo deployment/my-app-deployment 
```