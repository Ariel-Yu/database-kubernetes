# Docker CLI
- [docker](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/docker-cli.md#docker)
  - [Build a docker image](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/docker-cli.md#build-a-docker-image)
  - [Push a docker image to your docker hub](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/docker-cli.md#push-a-docker-image-to-your-docker-hub)
  - [Run a docker image](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/docker-cli.md#run-a-docker-image)
  - [Execute an iteractive bash shell inside a running docker image (container)](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/docker-cli.md#execute-an-iteractive-bash-shell-inside-a-running-docker-image-container)
- [docker image](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/docker-cli.md#docker-image)
  - [View docker images](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/docker-cli.md#view-docker-images)
  - [Inspect docker images](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/docker-cli.md#inspect-docker-images)
  - [Remove docker images](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/docker-cli.md#remove-docker-images)
- [docker-compose](https://github.com/Ariel-Yu/knowledge-bases/blob/master/docker/docker-cli.md#docker-compose)

## docker

### Build a docker image
```
docker build -t <image_name> <image_location>
```
- Create a docker image with tag <image_name> in the location <image_location>

```
docker tag <source_image_name>[:<source_image_version>]|<source_image_id> <target_image_name>[:<targe_image_version>] -> Push the image to central registry
docker tag <source_image_name>[:<source_image_version>]|<source_image_id> <registry_ip>:<registry_port>/<target_image_name>[:<target_image_version>] -> Push the image to local registry
docker push <registry_ip>/<image_name>
```

### Push a docker image to your docker hub
```
docker tag <image_name> <your_docker_hub_account>/<image_name>
docker push <your_docker_hub_account>/<image_name>
```
- ex: docker tag my-ubuntu arielyu0531/my-ubuntu
- ex: docker push arielyu0531/my-ubuntu

### Run a docker image
```
docker run <image_name>
```
- Run docker image <image_name>

```
docker run <image_name> <executable_command> <parameters>
```

Dockerfile:
```
FROM Ubuntu
# Default command
CMD ["bash"]
```
- Replace default command `bash` with parameters
- ex: `docker run new_ubuntu sleep 5`
  - Executable command: sleep
  - Parameter: 5

```
docker run --entrypoint <executable_command> <image_name> <parameters>
```

Dockerfile:
```
FROM Ubuntu
# Default executable command
ENTRYPOINT ["sleep"]
# Default parameter
CMD ["5"]
```
- Replace default entrypoint `sleep` and parameters `5`
- ex: `docker run --entrypoint sleep2 new_ubuntu 10`
  - Executable command: sleep2
  - Parameter: 10

### Execute an iteractive bash shell inside a running docker image (container)
```
docker exec -t <container_id> /bin/bash
```

## docker image

### View docker images
```
docker images
docker images -a
```
- List all the docker images in local cache

```
docker images -q
docker images --no-trunc
```
- `-q`: Only list the IDs of images
- `--no-trunc`: Don't truncate output

```
docker images -f "dangling=true"
```
- `-f` or `--filter`
- `dangling=true`: untagged images

### Inspect docker images
```
docker image inspect <image_name>
```
- Display detailed information of (an) image(s)

### Remove docker images
```
docker image rm <image_name>
```
- Remove docker image <image_name>

```
docker rmi $(docker images --filter "dangling=true" -q --no-trunc)
docker image prune
```
- Remove untagged images

```
docker image prune -a
```
- Remove docker images that are not referenced by any container

## docker-compose
```
docker-compose [--verbose] up [--build]
```
- --verbose: Give process details
- --build: Build images before starting containers
- Should be in the same directory of the docker-compose.yml

```
docker-compose run [application-name] [language exe command] [file_name absolute path]
docker-compose run --name [customized_contianer_name] [application-name] [language exe command] [file_name with absolute path]
```
- ex: docker-compose run pykafka_benchmark python3 /usr/src/app/test_pykafka_producer.py

```
docker-compose down
```
- Kill and remove all containers from the current docke_compose.yml
