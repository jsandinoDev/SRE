# Scheduling


### Manual Scheduling

The function of the scheduling is to check wich node does not have the nodeName attribute

To manually schedule a pod you can
- Add the nodeName in the definition file
- Create a binding and add this binding in the CLI command creation

---

### Labels and selectors

- Labels: properties attach to each item
- Selector: help filter these items

How to add labels
```yaml
  labels: 
    app: myapp
    tier: front-end
```

How to select them
```shell
kubectl get pods --selector app=myapp
```

**Annotations**: Used to record other details for integration purpuse. Ex:

How to add labels
```yaml
  labels: 
    app: myapp
    tier: front-end
  annotations:
    buildversion: 1.34
```

### Taints and Tolerations

Tells the node what type of pods accept based on the toleration
****
Taint a node (add repelent)
```shell
# Tain-effect -> is what happends to the pods that don't tolerate this taint
# Ex (NoSchedule | PreferNoSchedule| NoExecute)
kubectl taint nodes node-name key=value:taint:effect

kubectl taint nodes node1 key=blue:NoSchedule


# Remove a taint from a node, the (-) in the KEY
kubectl taint node controlplane mortein:NoSchedule-

```

Can be declared in yml file
```YAML
#pod-definition.yml
apiVersion: v1
kind: Pod
metadata: 
  name: myapp-pod
  labels: 
    app: myapp
    tier: front-end
spec:
  containers:
  - name: nginx
    image: nginx

  tolerations:
  - key: "app"
    operator: "Equal"
    value: "blue"
    effect: "NoSchedule"
```

---

### Node Selectors

Is to organice the pods and nodes based on criterias. Example: Size, Resource, etc

First label the node

```shell
#Template
kubectl label nodes <node-name> <label-key>=<label-value>

# Real Example
kubectl label nodes node-1 size=Large
```

And the in the pods declaration file:
```YAML
#pod-definition.yml
apiVersion: v1
kind: Pod
metadata: 
  name: myapp-pod
  labels: 
    app: myapp
    tier: front-end
spec:
  containers:
  - name: nginx
    image: nginx
  nodeSelector:
    size: Large
```

---

### Node Afinity

Ensure that pods are hosted in particular nodes

Types
- requiredDuringSchedulingIgnoredDuringExecution
- preferredDuringSchedulingIgnoredDuringExecution

```YAML
#pod-definition.yml
apiVersion: v1
kind: Pod
metadata: 
  name: myapp-pod
  labels: 
    app: myapp
    tier: front-end
spec:
  containers:
  - name: nginx
    image: nginx
  affinity:
    nodeAffinity:   
      requiredDuringSchedulingIgnoredDuringExecution
        nodeSelectorTerms:
        - matchExpressions:
            # Example1
          - key: size
            operator: In
            values:
            - Large
            - Medium

            # Example2
          - key: size
            operator: Exists
```

Add labels to nodes
```shell
kubectl label node node01 color=blue
```

---

### Resource Requirements and Limits

Values as

- 1 CPU  (a thread of a physical CPU Core)
  - 1 AWS vCPU
  - 1 GCP Core
  - 1 Azure Core
  - 1 Hyperthread

- 256 MI | 1G(Gigabyte) | 1Gi (Gibibyte)  




To define resource requests:


```YAML
#pod-definition.yaml
apiVersion: v1
kind: Pod
metadata: 
  name: myapp-pod
  labels: 
    app: myapp
    tier: front-end
spec:
  containers:
  - name: nginx
    image: nginx
    ports:
      - containerPort: 8080
    resources:
        request:
          memory: "4Gi"
          cpu: 2
        limits:
          memory: "2Gi"
          cpu: 2  
  
```

##### Default Behavior
No limit 

#### Limit Range

```YAML
apiVersion: v1
kind: LimitRange
metadata: 
  name: cpuLimit
    resources:
        limits:
        - default:
            cpu: 500m
          defaultRequest:
            cpu: 500m
          max:
            cpu: "1"
          min:
            cpu: 100m
          type: container
```

```YAML
apiVersion: v1
kind: LimitRange
metadata: 
  name: memoryLimit
    resources:
        limits:
        - default:
            memory: 1Gi
          defaultRequest:
            memory: 1Gi
          max:
            memory: 1Gi
          min:
           memory: 500Mi
          type: container
```

---

### DaemonSets

> Are like replicasets, helps to deploy many instances of pod but runs a copy of my pod on each node of the cluster
> When a new node is added to the cluster, the daemon set will add the pod
> Ensures that one copy of the pod is always preset

Usefull for
- Monitoring Solution
- Logs Viewer
- Kube-proyx
```YAML
apiVersion: v1
kind: DaemonSet
metadata: 
  name: daemon-set
spec:
    selector:
        matchLabels:
            app: monitorin
    template:
        metadata:
            labels:
                app: monitorin
        spec:
            containers:
            - name: monitoring-agent
              iamge:  monitoring-agent
```


Add labels to nodes
```shell
kubectl get daemonsets

kubectl describe daemonsets monitorint

```
---

### Static Pods

- Created by the kubelet
- Deploy control plane components as static pods
- ignred by the kube-scheduler

---

### Priority Classes

Defined in a range of numbers
```shell
kubectl get priorityclass
```

Create priotity class
```YAML
apiVersion: scheduling.k8s.io/v1
kind: PriorityClass
metadata: 
  name: high-priority
value: 10000000000
description: "dasdasdad"
```

Associate with a POD
```YAML
#pod-definition.yml
apiVersion: v1
kind: Pod
metadata: 
  name: myapp-pod
  labels: 
    app: myapp
    tier: front-end
spec:
  containers:
  - name: nginx
    image: nginx
  priorityClassName: high-prio
```


---

### Multiple Schedulers

- k8 cluster can have multiple schedulers
- Must have diffenrent name
Create scheduler
```YAML
apiVersion: scheduling.k8s.io/v1
kind: KubeSchedulerConfiguration
profiles:
- schedulerName: my-scheduler
leaderElection:
  leaderElect: true
  resourceNamespace: kube-system
  resourceName: lock-obj
```


Depoly as pod
```YAML
#pod-definition.yml
apiVersion: v1
kind: Pod
metadata: 
  name: mycustom-sche
spec:
  containers:
  - command:
    - kube-schedule
    - --address=127.0.0.1
    - --kubeconfig=/etc/kubernetes/scheduler.config
    - --config=/etc/kubernetes/my-scheduler.yaml
    name: kube-scheduler
    image: k8s.grc.io/kube-scheduler-amd:v1.11.3
```

To add in a new pod:
```YAML
#pod-definition.yml
spec:
  containers:
  schedulerName: my-sche
```

---

### Configuring Scheduler Profiles

Go to docs, hube topic


