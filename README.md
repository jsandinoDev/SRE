# SRE

### DevOps vs SRE

- **DevOps**: DevOps focuses on creating new features and improvements
- **SRE**: focuses on ensuring the reliability and stability of the system

---

# Containers

## Docker

Components and Tech

- **Docker Engine**: is the heart of Docker technology, providing the necessary functionality to create and manage container lifecycle

  - Containerd -> container runtime
  - runC -> runC is responsible for spawning and running containers based on OCI (Open Container Initiative) specifications
  - libcontainer -> initially used libcontainer as its container execution library

- **Docker client**: command-line tool that allows users to interact with the Docker daemon (Docker Engine)

- **Docker Images**: lightweight, standalone, and executable packages that include the application and all its dependencies

- **Docker Registry**: mages are stored in registries, which are repositories for sharing and distributing container images

- **Docker compose**: is a tool for defining and running multi-container Docker applications

- **Docker swarm**: Docker's native clustering and orchestration solution

- **Networking and Storage Drivers**:Docker provides various networking and storage drivers that allow containers to communicate with each other and with external networks.

---

## Kubernetes

Kubernetes is a powerful container orchestration platform that consists of several key components working together to manage and deploy containerized applications.

Kubernetes functionalities:

- Deployment: Kubernetes automates the deployment of containerized applications across a cluster of nodes.
- Scaling: It automatically scales applications up or down based on demand, ensuring optimal resource utilization.
- Load Balancing: Kubernetes evenly distributes traffic across different instances of your application, ensuring high availability and responsiveness.
- Service Discovery: It enables applications to discover and communicate with each other, regardless of their location within the cluster.
- Health Monitoring: Kubernetes monitors the health of your applications and automatically restarts them if they fail.
- Security: Kubernetes provides a robust security framework for managing access control and protecting your applications.
- Self-healing: Kubernetes restarts containers that fail, replaces containers, kills containers that don't respond to your user-defined health check, and doesn't advertise them to clients until they are ready to serve.
- Horizontal scaling: Scale your application up and down with a simple command, with a UI, or automatically based on CPU usage.

#### Components

- Control Plane Node ->
  Control plane nodes in Kubernetes play a critical role in managing the cluster's state and configuration. They are responsible for making global decisions about the cluster (like scheduling), as well as detecting and responding to cluster events (like starting up a new pod when a deployment's replicas field is unsatisfied). Here are the key components of control plane nodes:

      - API Server

  Serves as the front end for the Kubernetes control plane. The API server is responsible for handling requests, validating them, and updating the corresponding objects in the cluster. It exposes the Kubernetes API. - Cluster Data Store – etcd
  It’s the only stateful part of the cluster which persists the entire cluster configuration aka desired state and the current state of the cluster. - Controller Manager
  Manages controllers that regulate the state of the cluster. Controllers are responsible for maintaining the desired state and handling tasks like node management, replication, and endpoints. - Scheduler
  Assigns pods to nodes based on resource availability, constraints, and other policies. The scheduler makes decisions to ensure that the workload is evenly distributed across the cluster.

- Worker Node (Minion) -> Worker nodes in Kubernetes are the machines (physical or virtual) where your actual applications (containers) run. They are managed by the control plane and perform the requested, necessary workloads. Each worker node is a part of the Kubernetes cluster and has the necessary components to orchestrate and run applications. Here are the key components of a worker node:

      - Kubelet

  An agent running on each node that communicates with the control plane node's API server. It ensures that containers are running in a pod and reports back to the control plane about the node's status. - Container Runtime
  Responsible for managing the entire container lifecycle on the node. Containerd is one of the leading container runtimes. - Kube Proxy
  It is a Kubernetes agent installed on every node in the cluster. It is responsible for local cluster networking. It implements local IPTABLES or IPVS rules to handle routing and load-balancing of traffic on the Pod network. It monitors the changes that happen to Service objects and their endpoints. If changes occur, it translates them into actual network rules inside the node. Kube-Proxy is installed as an add-on during the installation process, usually created as a DaemonSet.

- Pod: A pod is the smallest deployable unit in Kubernetes, representing a single instance of a running process in a cluster

- ReplicaSet: Manages the lifecycle of pods and ensures that a specified number of replicas for a pod are running at all times.

- Deployment: Provides declarative updates to applications

- Service: Defines a set of pods and a policy to access them.

- Volume: Manages storage and provides data persistence for containers

- Namespace: Provides a way to divide cluster resources into multiple virtual clusters.

- ConfigMap and Secret: ConfigMaps and Secrets are used to manage configuration data and sensitive information (such as passwords or API keys) separately from the application code.

- Kubernetes Dashboard: A web-based UI for visually managing and monitoring the Kubernetes cluster

---

### Real Examples

#### Connect Google Cloud VM Instance with Virtual Box Ubuntu

- Generate SSH in ubuntu

```bash
ssh-keygen -t rsa -f ~/.ssh/josue-gcp -C "username
```

- This creates:

  - Private key: ~/.ssh/josue-gcp
  - Public key: ~/.ssh/josue-gcp.pub

- Run this to print:

```
cat ~/.ssh/josue-gcp.pub
```

- Add ssh key in GoogleCloud
