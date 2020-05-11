# docker - Docker image and container command line interface
------------------------------------------------------------
login to a container given only container name
```sh
docker exec -it `docker ps \
                 | sed -n '/<CONTAINER_NAME_HERE>/p' \
                 | awk '{print $1}'` bash
```

modify it to be your DB user
```sh
docker exec -it `docker ps \
                 | sed -n '/<CONTAINER_NAME_HERE>/p' \
                 | awk '{print $1}'` psql -U postgres
```

stop all containers
```sh
docker kill $(docker ps -q)
```
remove all containers
```sh
docker rm $(docker ps -a -q)
```
remove all images
```sh
docker rmi $(docker images -q)
```
combined stop, remove containers, and remove images command
```sh
docker kill $(docker ps -q) --force; \
docker rm $(docker ps -a -q) --force ; \
docker rmi $(docker images -q) --force
```
run pgsql
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
      - "5432:5432"
    expose:
      - "5432"
```
run pgadmin4
```sh
docker pull dpage/pgadmin4

docker run -e "PGADMIN_DEFAULT_EMAIL=dosterm@wit.edu" \
           -e "PGADMIN_DEFAULT_PASSWORD=password" \
           --network="host" <container-id>
```
or if you are lazy
```sh
alias pgadmin4="docker run -e "PGADMIN_DEFAULT_EMAIL=dosterm@wit.edu" \
                           -e "PGADMIN_DEFAULT_PASSWORD=password" \
                           --network="host" \
                           `docker image ls | sed -n '/pgadmin4/p' | awk '{print $3}'`"
```
