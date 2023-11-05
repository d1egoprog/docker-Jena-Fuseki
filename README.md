# Jena Fuseki UI - Dockerized Alternative

This repository is dedicated to expose and track a customized Docker Image of the traditional [Jena Fuseki for Docker](https://jena.apache.org/documentation/fuseki2/fuseki-docker.html). This build intends to be used as a dedicated service to provide for personal or small research teams.

A ready-to-use [image](https://hub.docker.com/r/d1egoprog/jena-fuseki) from Docker Hub is provided, along with the [deploy instructions](#deploy-alternatives). The current supported version is 4.9.0.

**DISCLAIMER:** this is **not an official documentation** guide. 

## Deploy Alternatives

To deploy the prebuilt docker image, two options are provided: use the `docker compose` tool from the `docker` command from the CLI utility.

The image needs the `INPUT_KG` as the default database for making queries. In this repository provides the `example.ttl` file.

### Deploy using Docker CLI

Directly run the `docker` command like the following example. For more information, check the [Official Documentation](https://jena.apache.org/documentation/fuseki2/)

``` Docker
docker run -v ./logs:/opt/jena-fuseki/logs -v ./example:/opt/jena-fuseki/input -e INPUT_KG=input/example.ttl -p 3030:3030 d1egoprog/jena-fuseki:4.9.0-web
```

### Deploy using docker-compose

Download the prepared `compose.yaml` file from the repository via `wget` and execute the command using the utility.

``` BASH
wget https://raw.githubusercontent.com/d1egoprog/docker-Jena-Fuseki/main/compose.yaml
docker compose -p jena-fuseki up -d
```

The previous lines will download and run the following docker compose file.

``` YAML
version: '3.7'

services:
  server:
    environment:
      - INPUT_KG=input/example.ttl
    volumes:
    - ./example:/opt/jena-fuseki/input
    - ./logs:/opt/jena-fuseki/logs
    ports:
      - 3030:3030
    image: d1egoprog/jena-fuseki:4.9.0-web
```

To check the functionality, you can open a web browser window on [localhost:3030](http://localhost:3030). 

Happy hacking!! 🖖🖖.

## Contact

If you have any questions in deployment or if any error is found, please contact me or open an issue. And contributing is always welcome. The [Github repository Issues](https://github.com/d1egoprog/docker-Jena-Fuseki/issues).