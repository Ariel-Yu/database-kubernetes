# Docker Container Paths

## Docker info
`docker info`

* Docker file location on the local machine
```
~/Library/Containers/com.docker.docker/Data/vms/0/tty
```
* Docker root path within the virtual image
```
/var/lib/docker
```

## See docker root directory in the virtual environment
```
screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty
ls -la /var/lib/docker
```
* See all the running screen sessions
`screen -ls`

* Detach a running screen sessions
`screen -r [id]`

## See the internal structure of a docker image
1. screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty
2. cd /var/lib/docker/overlay2
3. cd [image_path]
    - `docker image inspect [image_name] | grep Lower` → Get image_path

## Reference
- https://www.freecodecamp.org/news/where-are-docker-images-stored-docker-container-paths-explained/ 
- https://phase2.github.io/devtools/common-tasks/ssh-into-a-container/

