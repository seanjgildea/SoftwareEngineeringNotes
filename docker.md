# Docker Notes

- Everytime you run a new container you get a new unique ID
- Containers are just processes


# Docker Commands

- docker container stop [first few digits of container id]
- docker container ls ( shows only running containers)
- docker container ls -a ( shows all containers )
- docker container rm -f [first few digits of container id]
- docker container inspect
- docker container stats (streaming view of container data, CPU %)


# Docker Flags

--detach (run a container in the background and return the container id)



# Shortcuts

- docker run --name mongo -d mongo
- docker run --name mymysql2 -e MYSQL_ROOT_PASSWORD=password -d mysql:tag
