# ROS2 prereading

# Docker Usage
## Introduction

Docker is a platform designed to simplify the creation, deployment, and running of applications by using 
containers. Containers allow developers to package an application with all of its dependencies into a 
standardized unit for software development. This document covers how to use Docker commands, build images for 
different architectures, and write Dockerfiles.
## Basic Docker Commands
### Docker Pull

The docker pull command is used to download images from a Docker registry.

```bash
docker pull <repository>:<tag>
```
+ `<repository>`: The name of the image repository.
+ `<tag>`: The specific version or tag of the image.

For example:

```bash
docker pull ubuntu:20.04
```

This command pulls the Ubuntu 20.04 image from Docker Hub.

### Docker Run

The docker run command creates and starts a new container from a specified image.

```bash
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```
Common options include:

+ `-d`: Run the container in detached mode (in the background).
+ `-p`: Publish a container's port to the host.
+ `-v`: Bind mount a volume.
+ `--name`: Assign a name to the container.
+ `-it`: interactive mode.
+ `--rm`: Automatically remove the container when it exits.
+ `--network`: Connect the container to a network.
+ `--env`: Set environment variables.
+ `--entrypoint`: Override the default entry point.

Example:

```bash
docker run -d -p 8080:80 --name my_nginx nginx
```
This command runs an Nginx container in the background, mapping port 80 of the container to port 8080 on the host.

### Docker Exec

The `docker exec` command runs a command in a running container.

```bash
docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
```

Options:

- `-i`: Keep STDIN open even if not attached.
- `-t`: Allocate a pseudo-TTY.

Example:

```bash
docker exec -it my_nginx /bin/bash
```

This opens an interactive bash shell inside the `my_nginx` container.

### Docker PS

The `docker ps` command lists running containers.

```bash
docker ps [OPTIONS]
```
Common options:
+ `-a`: Show all containers (running and stopped).
+ `-q`: Only display container IDs.

### Docker Stop

The `docker stop` command stops a running container.

```bash
docker stop CONTAINER [CONTAINER...]
```

### Docker image

The `docker image` command manages images.

```bash
docker image [OPTIONS] COMMAND [ARG...]
```

Common commands:
+ `ls`: List images.
+ `rm`: Remove images.

Example:

```bash
docker image ls
```

This command lists all images on the system.

## Writing Dockerfiles

A Dockerfile is a script containing instructions on how to build a Docker image.

### Dockerfile Instructions

#### FROM

Sets the base image for subsequent instructions.

```dockerfile
FROM ubuntu:20.04
```

#### COPY

Copies files or directories from the host to the image.

```dockerfile
COPY <src> <dest>
```

Example:

```dockerfile
COPY . /app
```

#### RUN

Executes a command in a new layer and commits the results.

```dockerfile
RUN apt-get update && apt-get install -y python3
```

#### ENTRYPOINT

Configures a container to run as an executable.

```dockerfile
ENTRYPOINT ["executable", "param1", "param2"]
```

Example:

```dockerfile
ENTRYPOINT ["python3", "app.py"]
```

#### SHELL

Overrides the default shell used by the shell form of commands.

```dockerfile
SHELL ["executable", "parameters"]
```

Example:

```dockerfile
SHELL ["/bin/bash", "-c"]
```

#### ENV

Sets environment variables.

```dockerfile
ENV <key>=<value>
```

Example:

```dockerfile
ENV APP_ENV=production
```

#### LABEL

Adds metadata to the image.

```dockerfile
LABEL <key>=<value>
```

Example:

```dockerfile
LABEL maintainer="you@example.com"
```

#### ARG

Defines a variable that users can pass at build-time.

```dockerfile
ARG <name>[=<default value>]
```

Example:

```dockerfile
ARG VERSION=1.0
```

#### RUN

Executes a command in a new layer and commits the results.

```dockerfile
RUN pip3 install numpy
```

#### WORKDIR

Sets the working directory for subsequent instructions.

```dockerfile
WORKDIR /app
```

### Example Dockerfile

Below is an example Dockerfile that uses many of the instructions described above.

```dockerfile
FROM python:3.10

LABEL maintainer="you@example.com"
ENV APP_HOME=/app
WORKDIR $APP_HOME

COPY . $APP_HOME

RUN pip install --no-cache-dir -r requirements.txt

ENTRYPOINT ["python3", "main.py"]
```

This Dockerfile:

- Sets a Python 3.10 image as the base.
- Sets a maintainer label.
- Defines an environment variable `APP_HOME`.
- Sets the working directory.
- Copies the current directory contents into the image.
- Installs Python dependencies.
- Sets the entry point to run `main.py`.

## Building the Docker Image

To build an image using the Dockerfile:

```bash
docker build -t myusername/myapp:latest .
```

- `-t`: Tags the image with a name and optionally a tag.
- `.`: Specifies the build context (current directory).

## Additional Topics

### Environment Variables and Build Arguments

#### Using ARG and ENV Together

You can use `ARG` to pass variables at build-time and `ENV` to set environment variables in the image.

```dockerfile
ARG APP_VERSION=1.0
ENV VERSION=$APP_VERSION
```

Build the image with a specific version:

```bash
docker build --build-arg APP_VERSION=2.0 -t myapp:2.0 .
```

### Dockerignore File

Use a `.dockerignore` file to exclude files and directories from the build context.

Example `.dockerignore`:

```dockerignore
.git
node_modules
Dockerfile
```
___

# Installing ROS2

On the session on the 18th of October 2024 you should have one of the following options (you can also do both):
1. Install Docker and pull [ros:iron image](https://hub.docker.com/layers/library/ros/iron/images/sha256-76a2deab3da4dec0074b05cd55c4a13fb1b29d41a94bb8b9950dce20a3522264?context=explore)
2. Install [ROS2 iron](https://docs.ros.org/en/iron/Installation.html) on your machine 
