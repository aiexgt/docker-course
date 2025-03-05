
# DOCKER COMMANDS

## General Commands

### Images
`docker image ...`

### Containers
`docker container ...`

### Volumes
`docker volume ...`

### Networks
`docker network ...`

## Common Commands

### Download images
`docker pull ${image-name}`

### Delete
`docker ${general-command} rm -f ${id}`

### View
`docker ${general-command} ls -a`

### View logs
`docker container logs -f ${id}`

### Inspect container
`docker exec -it ${id} /bin/sh`

### Change image name
`docker image tag ${old_name} ${new_name}`

### Push image
`docker push ${repo}`

## Specific Commands

### Create container mariadb
```
docker container run --detach `
-dp 3306:3306 `
--name world-db `
-e MARIADB_USER=example-user `
-e MARIADB_PASSWORD=user-password `
-e MARIADB_ROOT_PASSWORD=root-secret-password `
-e MARIADB_DATABASE=world-db `
--volume world-db:/var/lib/mysql `
--network world-app `
mariadb:jammy
```

### Create container phpmyadmin
```
docker container run `
--name phpmyadmin `
-d `
-e PMA_ARBITRARY=1 `
-p 8080:80 `
--network world-app `
phpmyadmin:5.2.0-apache
```
### Create container node and run
```
docker container run `
--name nest-app `
-w /app `
-dp 80:3000 `
-v "${pwd}:/app" `
node:18.20.5-alpine3.21 `
sh -c "yarn install && yarn start:dev"
```
### Create container postgres with volume
```
docker container run `
-d `
--name postgres-db `
-e POSTGRES_PASSWORD=123456 `
-v postgres-db:/var/lib/postgresql/data `
postgres:15.1
```
### Create pgAdmin container and expose
```
docker container run `
--name pgAdmin `
-e PGADMIN_DEFAULT_PASSWORD=123456 `
-e PGADMIN_DEFAULT_EMAIL=superman@google.com `
-dp 8080:80 `
dpage/pgadmin4:6.17
```

## BuildX

### Pull BuildX
`docker buildx create --name mybuilder --driver docker-container --bootstrap`

### Default build
`docker buildx use mybuilder`

### Create image and push
`docker buildx build --platform linux/amd64,linux/arm64,linux/arm/v7 --tag ${image} --push .`