# Logging and Monitoring


There is no solution itself in k8 to monitor, its necessary to use an external solution like: prometheus

Each node hvae the KUBELET and cADVISOR, in charge of sharing the metrics of node to the external solution


```yaml
minikube addons enable metrics-server

# stat for nodes
kubectl top node

# stats for pods
kubectl top pod

```



# Example

Create a event simulator pod "event-simulator"

```yaml
kubectl create -f event-simulator.yaml

kubectl logs -f event-simulator-pod event-simulator

```