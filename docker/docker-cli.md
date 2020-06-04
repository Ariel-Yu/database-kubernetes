# Docker CLI

## docker

```
docker build -t <image_name> <directory> -> Create a docker image with tag <image_name> in the directory <directory>
docker run <image_name> -> Run the docker image

docker tag <source_image_name>[:<source_image_version>]|<source_image_id> <target_image_name>[:<targe_image_version>] -> Push the image to central registry
docker tag <source_image_name>[:<source_image_version>]|<source_image_id> <registry_ip>:<registry_port>/<target_image_name>[:<target_image_version>] -> Push the image to local registry
docker push <registry_ip>/<image_name>

docker exec -it <container_id> /bin/bahs -> Execute an iteractive bash shell inside a running docker image (container)
```

## docker image

```
docker images -> List all the docker images in local cache
docker image -a -> List all the docker images in local cache

docker image rm <image_name> -> Remove docker image <image_name>

docker image inspect <image_name> -> Display detailed information of (an) image(s)
```

## docker-compose
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
