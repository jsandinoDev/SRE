# Kube Controller

- watch staus
- remediate situation
  

Node controller -> kube-apiserver

In charge of monitor heallth of the nodes

If some node is unreachable it assign the node as that and work with the orders to balance

- Node monitor period -> 5s
- Node monitor grace period -> 40s
- POD Eviction Timeout -> 5min

Replication controller  -> kube-apiserver

If a pod dies, creates another one

