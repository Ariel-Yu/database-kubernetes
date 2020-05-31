# Docker CLI

## docker

```
docker build -t <image_name> <directory> -> Create a docker image with tag <image_name> in the directory <directory>
docker run <image_name> -> Run the docker image

docker tab <source_image_name>[:<source_image_version>]|<source_image_id> <target_image_name>[:<targe_image_version>] -> Push the image to central registry
docker tag <source_image_name>[:<source_image_version>]|<source_image_id> <registry_ip>:<registry_port>/<target_image_name>[:<target_image_version>] -> Push the image to local registry
docker push <registry_ip>/<image_name>
```

## docker image

```
docker images -> List all the docker images in local cache
docker image -a -> List all the docker images in local cache

docker image rm <image_name> -> Remove docker image <image_name>

docker image inspect <image_name> -> Display detailed information of (an) image(s)
```
