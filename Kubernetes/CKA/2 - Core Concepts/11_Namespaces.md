# Nacespaces

Created automatic

- kube-system
- kube-public
- default

To comunicate between namespaces

Services
- web-pod
- db-service
- web-development

Use
```SHELL
mysql.connect("db-service")
mysql.connect("db-service.dev.svc.cluster.local")

# db-service -> service name
# dev -> namespace
# svc -> service
# cluster.local -> domain
```

Commands
```SHELL
kubectl get pods --namespace=kube-system

# Create pod in namespace
kubectl apply -f pod.yaml --namespace=dev

# Create namesppace
kubectl create namespace dev

# Get namespaces
kubectl get namespaces


#Get all pods from namespaces
kubectl get pods --all-namespaces

# Create pod in namespace
kubectl run edis --image=redis --namespace=finance
```

Create namespace
namespace-definition.yml
```yaml
apiVersion: v1
kind: Namespace
metada: 
    name: dev
```

Change namespace context
```SHELL
kubectl config set-context $(kubectl config current-context) --namespace=dev
```

### Resource Quota

Limit resources in a namespace
```yaml
apiVersion: v1
kind: ResourceQuota
metada: 
    name: resource-quota
    namespace: dev
```