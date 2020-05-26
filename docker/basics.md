# Docker basics

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

## Docker compose
```
docker-compose [--verbose] up [--build]
```
* --verbose: Give process details
* --build: Build images before starting containers
* Should be in the same directory of the docker-compose.yml

```
docker-compose run [application-name] [language exe command] [file_name absolute path]
docker-compose run --name [customized_contianer_name] [application-name] [language exe command] [file_name with absolute path]
```
Ex: docker-compose run pykafka_benchmark python3 /usr/src/app/test_pykafka_producer.py

```
docker-compose down
```
Kill and remove all containers from the current docke_compose.yml

# Reference
- https://docs.docker.com/get-started/overview/#docker-architecture
