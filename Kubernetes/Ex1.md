### Upgrade system

```BASH
sudo apt update && sudo apt upgrade -y
```

### Install dependecies

```BASH
sudo apt install ca-certificates curl gnupg lsb-release -y
```

### Install docker

```BASH
curl-fsSL https://get.docker.com/|sh

```

#### Enable start on boot

```
sudo systemctl enable --now docker

```

### Check docker service is running

```
sudo systemctl status docker
```

### Add current user to the docker group

```
sudo usermod -aG docker $USER
```

### Exit Shell and logging again

### Verify docker instalation

```
docker ps
```

---

## Manage Container lifecicly with docker

```
sudo docker container run hello-world
```

---

### Install Kb8

Kubectl

```
curl -sSL -O "https://dl.k8s.io/release/$(curl -sSL https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

```
chmod +x kubectl
sudo mv kubectl /usr/local/bin
```

### Install KIND

```[ "$(uname -m)" = "x86_64" ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64

```
