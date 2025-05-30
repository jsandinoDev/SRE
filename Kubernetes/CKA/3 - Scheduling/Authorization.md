# Access Controllers


## Authorization - RBAC


```YAML
#pod-definition.yml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata: 
  name: developer
rules:
- apiGrouos: [""]
  resources: ["pods"]
  verbs: ["create"]
  resourcesNames: ["orange, blue"]
```


## Admission Controllers
- AlwaysPullImages
- DefaultStorageClass
- EvetnRateLimit
- ...

View  Enabled ADmission COntrollers

```shell
kube-apiserver -h | grep enable-admission-plugins
```

## Validating and Mutations Addmission Controllers

