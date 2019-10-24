# Docker commands

- `docker run container_name alternative_command`

  > creates and runs docker container

  > is equal to `docker create` and `docker start`

- `docker ps`

  > lists all running containers

  > `--all` (lists all, not only running, but also history)

- `docker create image_name`

  > creates the container and returns its id

- `docker start container_id`

  > runs the container with given id

  > `-a` option prints the output from the conteiner to standard output (attach)

- `docker system prune`

  > removes all the stopped containers, caches etc.

- `docker logs container_id`

  > returns all logs from the container

- `docker stop container_id`
  > sends SIGTERM to the process
- `docker kill container_id`
  > sends SIGKILL to the process
