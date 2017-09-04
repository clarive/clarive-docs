---
title: Running Clarive in Docker
---

Clarive can be installed and run in a Docker composer
setup. Docker composer will orchestrate a multi-image
install, with separate database and Clarive processes.

This is an official way to run Clarive in a docker container. This repository
provides a docker-compose configuration that will start Database, Web and
Dispatcher services.

### Prerequisites

A running docker daemon and have docker-compose v2 or greater installed.
There's can find documentation on the Docker website.

### Configuration

Create config/clarive.yml config from a template:

    cp config/clarive.example.yml config/clarive.yml

Create docker-compose.yml from a template:

    cp docker-compose.example.yml docker-compose.yml

### Starting

    docker-compose up

or in detached mode

    docker-compose up -d

### Connecting

Open your browser and navigate to `http://localhost:8080`

    docker-compose up

    http://localhost:8080



