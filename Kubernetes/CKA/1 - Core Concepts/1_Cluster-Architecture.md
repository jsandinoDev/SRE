# Cluster Architecture

## Components
- Worker nodes
- Master node -> control plane
- ETCD cluster -> database to store
- kube-scheduler -> identify the right time to place a node based on the container polic
- Controllers
  - Controller-manager
  - Node-controller
  - Replication-controller
- kube-apiserver -> responsable to coordinate or the previous components 

### Components running in the worker nodes
- Kubelet -> agent that runs on each node of a cluster / listen to instrucctions
- kube-proxy -> ensure necessary rules for the communication between the worker nodes 


Can be separate like this:

Master
- ETCH cluster
- kube-apiserver
- kube controller manager
- kube scheduler

Working nodes
- kubelet
- kubeproxy
- docker, etc

---


