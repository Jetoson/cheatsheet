## container

```bash
docker container ls
```

```bash
docker container ls -a
```

```bash
docker container run -d --publish 8080:80 --name "<OPTIONAL_NAME>" "<IMAGE_NAME>"
```

```bash
docker container run -d --network "<NETWORK_ID>" --name "<OPTIONAL_NAME>" "<IMAGE_NAME>"
```

```bash
docker container run -d --network "<NETWORK_ID>" --network-alias "<ALIAS_NAME>" "<IMAGE_NAME>"
```

```bash
docker container run -d -v "<VOLUME_NAME>:<MOUNT_PATH_ON_CONTAINER>" "<IMAGE_NAME>"
```

```bash
docker container run -d -v "<PATH_TO_LOCAL_DIRECTORY>:<MOUNT_PATH_ON_CONTAINER>" "<IMAGE_NAME>"
```

```bash
docker container stop "<CONTAINER_ID>"
```

```bash
docker container logs "<CONTAINER_ID_OR_NAME>"
```

```bash
docker container top "<CONTAINER_ID>"
```

```bash
docker container rm -f "<CONTAINER_ID>"
```

```bash
docker container prune -f
```

```bash
docker container inspect "<CONTAINER_ID>"
```

```bash
docker container stats
```

```bash
docker container run -it "<IMAGE_NAME>" bash
```

```bash
docker container run --rm -it "<IMAGE_NAME>" bash
```

```bash
docker container start -ai "<CONTAINER_ID>"
```

```bash
docker container exec -it "<CONTAINER_ID>" bash
```

```bash
docker container port "<CONTAINER_ID>"
```

## network

```bash
docker network ls
```

```bash
docker network inspect "<NETWORK_ID>"
```

```bash
docker network create "<NAME>"
```

```bash
docker network create --driver "<DRIVER_ID>" "<NAME>"
```

```bash
docker network connect "<NETWORK_ID>" "<CONTAINER_ID>"
```

```bash
docker network disconnect "<NETWORK_ID>" "<CONTAINER_ID>"
```

## image

```bash
docker image ls
```

```bash
docker image history "<IMAGE_NAME>"
```

```bash
docker image inspect "<IMAGE_NAME>"
```

```bash
docker image tag "<IMAGE_NAME>:<TAG>" "<USERNAME>/<IMAGE_NAME>:<TAG>"
```

```bash
docker image push "<REPOSITORY>:<TAG>"
```

```bash
docker image build -t "<TAG_NAME>" "<BUILD_CONTEXT>"
```

```bash
docker image rm "<IMAGE_ID>"
```

```bash
docker image prune -af
```

## volume

```bash
docker volume ls
```

```bash
docker ps -a --filter volume=<VOLUME_NAME>
```

## dockerfile

```Dockerfile
VOLUME /path/to/directory
```

## docker-compose

```bash
docker-compose up -d
```

```bash
docker-compose down -v
```

```bash
docker-compose build
```

```bash
docker-compose logs
```

```bash
docker-compose ps
```

```bash
docker-compose top
```

## swarm

```bash
docker node ls
```

```bash
docker service create "<IMAGE_NAME>" "<COMMAND>"
```

```bash
docker service ls
```

```bash
docker service ps "<SERVICE_ID>"
```

```bash
docker service update "<SERVICE_ID>" --replicas 3
```

```bash
docker service rm "<SERVICE_NAME>"
```

## misc

```bash
docker version
```

```bash
docker login
```

```bash
docker logout
```

```bash
docker swarm init
```
