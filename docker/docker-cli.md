# Docker CLI

## docker

```
docker build -t <image_name> <directory> -> Create a docker image with tag <image_name> in the directory <directory>
docker run <image_name> -> Run the docker image

docker tag <image_name:image_version> <registry_ip>/<image_name>
docker push <registry_ip>/<image_name>
```

## docker image

```
docker images -> List all the docker images in local cache
docker image -a -> List all the docker images in local cache

docker image rm <image_name> -> Remove docker image <image_name>

docker image inspect <image_name> -> Display detailed information of (an) image(s)
```
