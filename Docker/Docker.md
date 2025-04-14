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
