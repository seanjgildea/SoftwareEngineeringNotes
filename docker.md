# Docker Cert Study Notes

- Everytime you run a new container you get a new unique ID
- Containers are just processes
- Docker bridge is a container level network that acts as sort of a VPC


# Docker Commands

- docker container stop [first few digits of container id]
- docker container ls ( shows only running containers)
- docker container ls -a ( shows all containers )
- docker container rm -f [first few digits of container id]
- docker container inspect (show metadata about the container)
- docker container stats (live performance data for all containers)
- docker container run -it (start new container interactively)
- docker container start -ai [name of container] (restart container interactively)
- docker container exec -it mysql bash (starts mysql container in bash)
- docker pull alpine ( 5mb dist of linux )
- docker container run -it alpine sh ( start apline in sh shell, bash not included in alpine )
- docker network ls
- docker network inspect
- docker network create --driver
- docker network connect/disconnect [id of network] [id of container]
- --

# Docker Flags

--detach (run a container in the background and return the container id)



# Shortcuts

- docker run --name mongo -d mongo
- docker run --name mymysql2 -e MYSQL_ROOT_PASSWORD=password -d mysql:tag
