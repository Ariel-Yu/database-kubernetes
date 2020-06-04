# Docker basics

- [Docker engine](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/basics.md#docker-engine)
- [Docker registries](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/basics.md#docker-registries)
- [Docker objects](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/basics.md#docker-objects)
- [Reference](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/basics.md#reference)

## Docker engine
Docker engine is a server-client application which builds and containerizes other applications. Docker engine includes:

- Docker server:
A server with a long running daemon process called  ***dockerd***  (Docker daemon for me is the backend of docker that processes requests from docker APIs.)

- Docker APIs:
Interfaces that other applications can use to instruct docker daemon

- Docker command line interface:
A CLI client  ***docker***  that can be used from terminals to instruct docker daemon. Docker CLI uses docker APIs to interact with docker daemon
    - An application can interact with docker daemon through either docker APIs or docker CLIs.
    
## Docker registries
Docker registry is the store of Docker images.

## Docker objects

- Images
    - A Docker image is a set of read-only instructions for creating a Docker container.
    - A Docker image is usually built on top of another Docker image
    - A Dockerfile is used to build up a Docker image. Each instruction within a Dockerfile will build a layer of a Docker image.

- Containers
    - A container is a running instance of a Docker image.

- Services
    - Services allow the containers to be scaled to multiple Docker Daemons. Each Docker Daemon will communicate with each other through Docker APIs. 

## Reference
- https://docs.docker.com/get-started/overview/#docker-architecture
