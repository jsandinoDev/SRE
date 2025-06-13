# Configure Applications

Configure Docker Images


Add 5 sec deplay permantent from image create own
```dockerfile
FROM Ubuntu
CMD sleep 5

# Can be
CMD sleep 5
CMD ["sleep", "5"]
```

Using entreypoint
```dockerfile
FROM Ubuntu

ENTRYPOINT ["sleep"]

CMD ["5"] # This is to avoid error, default argument 

# So to call it can be
docker run ubutu-sleeper 10
```

#### Create pod based on that


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
  - name: ubutu-sleeper
    image: ubutu-sleeper
    command: ["sleep2"] # replace entrypoint
    args: ["10"]
```

### Environments in K8

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
  - name: ubutu-sleeper
    image: ubutu-sleeper
   
    env:
      - name: APP_COLOR
        value: pink
```

---
#### Config Maps

Create config map
```YAML
kubectl create configmap \
        <config-name> --from-literal=<key>=<value>

   #ex     app-config --from-literal=APP_COLOR=blue

   #ex2     app-config --from-file=app_config.properties


kubectl get configmaps


# Declarative way
apiVersion: v1
kind: ConfigMap
metadata: 
  name: config
data:
    APP_COLOR: blue
    APP_MODE: prod
```

####  Add into POD
ENV
```YAML
    envFrom:
      - configMapRef:
            name: config
```
SINGLE ENV
```YAML
    env:
      - name: APP_COLOR
        valueFrom:
        configMapRef:
            name: app-config
            key: APP_COLOR
```

VOLUME
```YAML
    volumes:
    - name: app-config-volume
        name: app-confg
```
--- 
#### Secrets


```YAML
kubectl create secrect generic \
        <secret-name> --from-literal=<key>=<value>

        <secret-name> --from-literal=<key>=<value>
```

Declarative file
```YAML
# Declarative way
apiVersion: v1
kind: Secret
metadata: 
  name: app-secret
data:
    DB_HOST: sql # this should be enconded
    DB_USER: root
    DB_PASSWORD: password


#### TO enconde
echo -n "mysql" | base64
echo -n "mysql" | base64  --decode
```
  
```YAML
kubectl get secrets / describe secret

kubectl get secret app-secret -o yaml
```

Config POD


```YAML
    env:
      - name: APP_COLOR
        valueFrom:
            secretKeyRef:

    envFrom:
      - secretRef:
            name: app-secret
```