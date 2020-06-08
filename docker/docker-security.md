# Docker Security
- Containers share the same OS kernel with their host machine
- Containers are isolated by the namespaces. Each container and the host machine have their own namespaces
  
## Process isolation
- Each container can only see the processes in its namespace
- Container namesapces are under host namespace which means that, one can see all the processes running on the host as well as on the containers
- A process running on a containers will have different process ids when seen from the host machine
- View the list of processes `ps aux`

## User isolation
1. Run docker image with given user id

`docker run <image_name> --user=<user_id>`

```
FROM ubuntu
USER <user_id>
```

2. Run docker image with given capabilities
- Root users of containers and the host have different permissions (linux capabilities)

`docker run <image_name> --cap-add <capability>`

`docker run <image_name> --cap-drop <capability>`

`docker run <image_name> --priviledged`
