# Docker commands

- `docker run container_name/id alternative_command`

  > creates and runs docker container

  > is equal to `docker create` and `docker start`

  > `-p (localhost port):(container port)` port mapping

  > `-d` starts container in the background

- `docker ps`

  > lists all running containers

  > `--all` (lists all, not only running, but also history)

- `docker create image_name`

  > creates the container and returns its id

- `docker start container_id`

  > runs the container with given id

  > `-a` option prints the output from the container to standard output (attach)

- `docker system prune`

  > removes all the stopped containers, caches etc.

- `docker logs container_id`

  > returns all logs from the container

- `docker stop container_id`

  > sends SIGTERM to the process

- `docker kill container_id`

  > sends SIGKILL to the process

- `docker exec -it container_id command`

  > executes an additional command in the container

  > `-it` allows us to provide input to the container

- `docker build .`

  > builds a docker image from Dockerfile in current directory

  > Example:

  ```dockerfile
  # Use an existing docker image as a base
  FROM alpine

  # Any following command will be executed relative to this path in the container
  WORKDIR /usr/app

  # Copy files to docker container
  COPY ./ ./

  # Download and install a dependency
  RUN apk add --update redis

  # Tell the image what to do when it starts as a container
  CMD ["redis-server"]
  ```

  > `-t dockerId/project_name:version` creates a tag that can be used instead of id

## Docker Compose

- separate CLI that gets installed along with Docker
- Used to start up multiple Docker containers at the same time
- Automates some of the long-winded arguments passed to `docker run`

> Example of `docker-compose.yml`:

```yml
version: "3" # version of docker compose
services:
  redis-server:
    image: "redis"
  node-app:
    restart: always
    build: . # look into current directory for Dockerfile
    ports:
      - "8081:8081"
```

### Commands

- `docker-compose up`

  > equivalent of `docker run myimage`

  > `--build` = `docker build .` + `docker run myimage` - used when you need to rebuild images that are in the docker compose file

  > `-d` at the end to run in the background

- `docker-compose down`

  > stops the containers

- `docker-compose ps`
  > same as `docker ps`

| docker compose restart policies |                                                                            |
| ------------------------------- | -------------------------------------------------------------------------- |
| "no"                            | Never attempt to restart this . container if it stops or crashes (default) |
| always                          | If this container stops for any reason always attempt to restart it        |
| on-failure                      | Only restart if the container stops with an error code                     |
| unless-stopped                  | Always restart unless we forcibly stop it                                  |
