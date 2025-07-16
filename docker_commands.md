### CONTAINER COMMANDS

```
docker ps			        -> show containers runnning
docker ps -a                -> show all continers (running or not)
```

```
docker run <image_name>	                            	-> run image
docker run <image_name:version>                     	-> pull and run image
docker run -d <image_name>	                            -> run the container in detached mode
docker run -p <hostport>:<containerport> <image_name>	-> setup a port
docker run --name <new_name> <image_name>               -> run a container with a custom name
docker run -e <enviroment_variable> = <value> <image>   -> set an enviroment variable
docker run -net <network_name> <image>                  -> config a network for the image
docker run -v <volume_name>:<volume_path> <image>       -> configure volume
```

```
docker container stop <id_container>	-> stop container
docker container start <id_container>	-> resume container
docker container rm <name_container>    -> delete a container
docker container prune                  -> delete all stopped containers
```

```
docker logs <id_container>	            -> show container logs
docker exec -it <id_container> <route>  -> enter the container
```

### IMAGES COMMANDS

```
docker login <REGISTRY_URL>         -> login to a registry
docker pull <image_name>	        -> pull image from register
docker push <name>:<tag>            -> upload an image to a registry
docker build <path>                 -> build a image from a Dockerfile
```

```
docker images			            -> list images
docker rmi <name_image>             -> delete images
```

```
docker image tag <current_name>:<current_tag> <new_name>:<new_version>     -> create alias for a image
```

### NETWORKS COMMANDS

```
docker network ls		                    -> list all networks 
docker network create <name_new_network>    -> create a new network 
```

### COMPOSE COMMANDS

```
docker compose up                   -> start a container
docker compose down                 -> stop and delete the containers
```

### DOCKER COMPOSE FILE

```
services:
    <name_container>:
        image: <name_image> OR build: <path>
        ports:
            - "<host_port>:<container_port>"
        environment:
            - <enviroment_variable1> = <value>
            - <enviroment_variable2> = <value>
        volumes:
            - <dir_host>:<dir_container>
            ....
    <name_container2>:
        ...
```

### DOCKERFILE FILE: plain text file that containing set of instructions to build a Docker image

```
FROM <image_name>                   -> sets the base image
ARG <variable_name> = <value>       -> define a global variable
ENV <enviroment_variable> = <value> -> sets enviroment_variable
WORKDIR <path>                      -> sets the working directory
COPY <source_path> <host_path>      -> adds files and folders to image filesystem
RUN <command_1> && <command_2> ...  -> execute shell commmands during build time
EXPOSE <port>                       -> documents which ports the container will listen on
USER <user>                         -> set user and group ID 
VOLUME <path>                       -> define a extern directory to store data from container
CMD <command>                       -> provides default command to run at container start
ENTRYPOINT <command>                -> define a command that will always be executed
```
