# Docker

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

### Docker Images

DockerFile --> Create an image

Can be

- tagged (named) / -t docker tag ..
- listed / docker images
- analyzed / docker image inspect
- removed / docker rmi, docker prune

```yaml

FROM node

WORKDIR /app
# sets docker that all the subsequence commands have to run inside /app folder

COPY package.json /app

RUN npm install
# Here because of the layers (optimization)
# Every time there is change in the src code there will be no need of run again npm install
# Docker will use the cache of this command

# COPY . ./  -> a way to do the line 7
COPY . /app
# 1 (.) path outside the dockerfile -> copy into the image
# 2(.) path inside the image  -> where to copy in the image
# create a snapshot of the source code


EXPOSE 80
# a docker container is ISOLATED
# have its own network
# expose a port to the local machine

CMD  ["node",  "server.js"]
# not executed when an image is create but when a container is created
```

```
docker build .
```

Name and tag

```
docker build -t api:-node:0 .
```

---

### Containers

The running "unit of software"

Can be:

- named / --name
- configured / --help
- listed / docker ps
- removed / docker rm

Commands

```


docker start "name"

docker stop "name"

docker container ps -a --> List all

docker container ps -a | grep "name" --> List and filter

docker container inspect "name"

docker attach

docker logs
```

Running Containers

```
-d -> detach (run in background)

-entrypoint -> override entrypoint set in dockerfike

-env -> pass env variables

--init

--it -> interactive mode

--mount --> add volume/bind mount

--name

--network

--publish -> share ports

--rm  --> Remove

```

Example

Run detach + ports

```
    docker run -p 3000:3000 -d 96577f2d608d30661a896d4f0268ebfdc63f7119dfa630d15f96d216740786d0
```

Run image/ generate it shell (it, tty) /delete after close(rm)

```
docker run --it --tty --rm ubuntu:22:04
```

Run in a volume mount

```
docker run -it -rm -mount source=my-volume, destination=/my-data/ ubuntu:22.04
```

Run in a bindmount

```
docker run -it -rm -mount --type=bind, source="{PWD}/my-data, destionation=/my-data/ ubunut:22.04
```

#### Networks

```
docker network create my-net

docker network ls

docker run -d --network my-net ubuntu:22.04
```

---

## Docker Compose

```
docker compose up -d

docker compose down

docker compose up --build -> force images to rebuild
```

Example:

```
version: "3.7"

services:

#docker run -dp 3000:3000 --network todo-app -e MYSQL_HOST=mysql -e MYSQL_USER=root -e MYSQL_PASSWORD=secret -e MYSQL_DB=todos getting-started:v2

  app:
    image: pablokbs/getting-started:v2
    ports:
      - 3000:3000
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

# docker run -d     --network todo-app --network-alias mysql     -v todo-mysql-data:/var/lib/mysql     -e MYSQL_ROOT_PASSWORD=secret     -e MYSQL_DATABASE=todos     mysql:5.7

  mysql:
    image: mysql:5.7
    volumes:
      - ./todo-mysql-data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

```
