# Overview

Nokia is providing SR Linux as a license free Docker image.
This is a great way to have a running SR Linux instance (or many instances) in just a few minutes.


## Basic Requirements

* Linux server/vm with minimum of 2 vCPU & 4GB RAM (more is better)
* [Docker](https://docs.docker.com/engine/install/)
* SR Linux Docker image (current version is 21.3.1)


## Quick Start

This will launch a single SR Linux instance suitable for basic navigation/inspection of the system.
See [Advanced](advanced/clab.md) and/or [ContainerLab](related.md) for an easy to create more interesting and usable labs.

!!! note
    Commands need to be run as `root` or a user with `sudo` privileges

Add SR Linux image to local Docker registry

```shell
docker image load -i 21.3.1-410.tar.gz
```

Launch SR Linux container with name "srlinux-dut1" using Docker CLI

```shell
docker run -t -d --rm --privileged \
  -u $(id -u):$(id -g) \
  --name srlinux-dut1 srlinux:21.3.1-410 \
  sudo bash /opt/srlinux/bin/sr_linux
```

Use `docker ps` to verify "srlinux-dut1" container is running

```shell
CONTAINER ID   IMAGE                             COMMAND                  CREATED        STATUS        PORTS             NAMES
75d3fdb25565   srlinux:21.3.1-410                "/tini -- fixuid -q …"   46 hours ago   Up 46 hours                     srlinux-dut1
```

Attach to SR Linux CLI

```shell
docker exec -it srlinux-dut1 sr_cli
```

See [Usage](usage/basics.md) for basic command examples


### Optional - Docker Compose

Make sure [Docker Compose](https://docs.docker.com/compose/install/) is installed.

Create this `docker-compose.yml` file

```yaml
version: "3"
services:
  srlinux:
    container_name: srlinux-dut1
    image: srlinux:21.3.1-410
    privileged: true
    user: "${CURRENT_UID}"
    command: sudo sh -c "/opt/srlinux/bin/sr_linux"
    restart: "no"
```

Launch using this command

```shell
CURRENT_UID=$(id -u):$(id -g) docker-compose up -d
```

Remove the container when done

```shell
CURRENT_UID=$(id -u):$(id -g) docker-compose down
```
