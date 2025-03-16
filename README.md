# Docker Compose - TestLink

TestLink is a web-based application to manage manual tests along with the software life cycle. Tests may vary from simple steps to more evolved processes, but each will provide simple steps to follow.

## Prerequisites

- Docker Engine 18.06.0+
  - **Linux:** Follow all the steps present in the [official documentation](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce)
- Docker Compose 1.22.0+
  - Follow all the steps present in the [official documentation](https://docs.docker.com/compose/install/)

## Set the Environment Variables

The file `.env.example` contains all the environment variables required.

Copy and paste the file `.env.example` with the name `.env` to make Docker Compose use the environment variables defined in this file:

```sh
cp .env.example .env
```

After that, set up the variables according to specific requirements of each deployment.  

## Building and Deploying the Containers

```sh
docker-compose up --build
```

It will build the containers and run the platform as specified in the file `docker-compose.yml`, opening a log screen with the logs of all the services started. 

## Connecting to TestLink

Once the containers are running, open a web browser and navigate to:

```
http://localhost:8080
```

You can log in using the credentials set in the `.env` file for `TESTLINK_USERNAME` and `TESTLINK_PASSWORD`.

## Stopping the Execution

If you are still in the log screen, press `Ctrl + C` just one time for a graceful stop, or two times to force stop.

To stop all containers created by Docker Compose, go to the folder where `docker-compose.yml` is located and run:

```sh
docker-compose down
```

To stop just one container:

```sh
docker stop my_container
```

## Other Useful Commands

Restart Docker (useful in critical situations):

```sh
sudo service docker restart
```

Check all containers and their status:

```sh
docker container ls
```

Enter the shell or bash of a particular container:

```sh
docker exec -it container_id /bin/bash
```

Stop all containers:

```sh
docker stop $(docker ps -a -q)
```

Delete all containers:

```sh
docker rm -f $(docker ps -a -q)
```

Delete all volumes:

```sh
docker volume rm $(docker volume ls -q)
```

Delete all container images:

```sh
docker rmi -f $(sudo docker images -q)
```
