# Docker

## Restart Docker daemon on macOS

```bash
open -F -g -n -b com.docker.docker
```

|flag|description|
|---|---|
|`-F`|open application with fresh state|
|`-b`|specify application bundle identifier|
|`-g`|do not bring application to foreground|
|`-n`|always open new instance of application|

## Ubuntu GPG un-signed

```bash
docker run --interactive --tty --security-opt seccomp:unconfined ubuntu:latest bash
```

## login to a container given only container name

```bash
docker exec -it $(docker ps | sed -n '/<CONTAINER_NAME_HERE>/p' | awk '{print $1}') bash
```

## modify it to be your DB user

```bash
docker exec -it $(docker ps | sed -n '/<CONTAINER_NAME_HERE>/p' | awk '{print $1}') psql -U postgres
```

## stop all containers

```bash
docker kill $(docker ps -q)
```

## Remove all containers

```bash
docker rm $(docker ps -a -q)
```

## Remove all images

```bash
docker rmi $(docker images -q)
```

## remove containers, and remove images command

```bash
docker kill $(docker ps -q) --force
docker rm $(docker ps -a -q) --force
docker rmi $(docker images -q) --force
```

## run pgsql

```yaml
version: '3'
services:
db:
image: postgres:9.6
network_mode: host
environment:
  - POSTGRES_DB=postgres
  - POSTGRES_USER=postgres
  - POSTGRES_PASSWORD=postgres
ports:
  - 5432:5432
expose:
  - '5432'
```

## run pgadmin4

```bash
docker pull dpage/pgadmin4
```

or

```bash
docker run \
  -e "PGADMIN_DEFAULT_EMAIL=dosterm@wit.edu" \
  -e "PGADMIN_DEFAULT_PASSWORD=password" \
  --network="host" <container-id>
```

or if you are lazy

```bash
docker run \
	-e 'PGADMIN_DEFAULT_EMAIL=dosterm@wit.edu' \
	-e 'PGADMIN_DEFAULT_PASSWORD=password' \
	--network='host' \
	$(docker image ls | sed -n '/pgadmin4/p' | awk '{print $3}')
```
