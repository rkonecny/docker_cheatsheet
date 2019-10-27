# Docker commands

- `docker run container_name/id alternative_command`

  > creates and runs docker container

  > is equal to `docker create` and `docker start`

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

  # Download and install a dependency
  RUN apk add --update redis

  # Tell the image what to do when it starts as a container
  CMD ["redis-server"]
  ```

  > `-t dockerId/project_name:version` creates a tag that can be used instead of id
