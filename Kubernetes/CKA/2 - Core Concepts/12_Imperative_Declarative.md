# Imperatve and Declarative

### Imperative

Use commands like:

```SHELL
# Create namesppace
kubectl create namespace dev
kubectl create namespace dev
kubectl edit namespace dev
...
```

### Declarative

Run commands based on a yaml file
Commands
```SHELL
# Create pod in namespace
kubectl apply -f pod.yaml --namespace=dev
```