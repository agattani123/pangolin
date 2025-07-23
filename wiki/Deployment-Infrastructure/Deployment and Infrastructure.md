<details>
<summary>Relevant source files</summary>

The following file was used as context for generating this wiki page:

- [docker-compose.yml](https://github.com/agattani123/pangolin/blob/main/docker-compose.yml)
</details>

# Deployment and Infrastructure

## Introduction

The provided `docker-compose.yml` file defines the configuration for deploying and running the "Pangolin" application in a development environment using Docker Compose. It specifies a single service named `app`, which represents the main application container. This introduction provides an overview of the deployment and infrastructure setup for the development environment.

## Application Service

The `app` service is the core component of the deployment configuration. It defines the settings and environment for running the application in a Docker container during development.

### Container Configuration

#### Build Context

```yaml
build:
  context: .
  dockerfile: Dockerfile.dev
```

The `build` section specifies that the Docker image for the `app` service should be built using the `Dockerfile.dev` file located in the current directory (`.`). This Dockerfile likely contains instructions for setting up the development environment and installing necessary dependencies.

#### Container Name

```yaml
container_name: dev_pangolin
```

The `container_name` option assigns a specific name to the running container instance, making it easier to identify and manage.

#### Ports

```yaml
ports:
  - "3000:3000"
  - "3001:3001"
  - "3002:3002"
```

The `ports` section maps host ports (left side) to container ports (right side). This configuration allows the application running inside the container to expose and communicate through these ports on the host machine.

#### Environment Variables

```yaml
environment:
  - NODE_ENV=development
  - ENVIRONMENT=dev
  - DB_TYPE=pg
```

The `environment` section sets environment variables within the container. These variables can be used by the application to configure its behavior or connect to external services. In this case, the variables indicate that the application is running in a development environment (`NODE_ENV=development`, `ENVIRONMENT=dev`) and is using a PostgreSQL database (`DB_TYPE=pg`).

#### Volumes

```yaml
volumes:
  - ./src:/app/src
  - ./server:/app/server
  - ./public:/app/public
  - ./messages:/app/messages
  - ./components.json:/app/components.json
  - ./next.config.mjs:/app/next.config.mjs
  - ./tsconfig.json:/app/tsconfig.json
  - ./tailwind.config.js:/app/tailwind.config.js
  - ./postcss.config.mjs:/app/postcss.config.mjs
  - ./eslint.config.js:/app/eslint.config.js
  - ./config:/app/config
```

The `volumes` section mounts local directories and files from the host machine into the container's filesystem. This allows the application code and configuration files to be shared between the host and the container, enabling live code changes and hot reloading during development.

#### Restart Policy

```yaml
restart: no
```

The `restart` option is set to `no`, which means the container will not automatically restart if it stops or crashes.

Sources: [docker-compose.yml](https://github.com/agattani123/pangolin/blob/main/docker-compose.yml)

## Conclusion

The provided `docker-compose.yml` file sets up the deployment and infrastructure for running the "Pangolin" application in a development environment using Docker Compose. It defines a single `app` service with configurations for building the Docker image, setting environment variables, mapping ports, mounting volumes for code and configuration files, and specifying a container name. This setup allows developers to work on the application code locally while leveraging the benefits of containerization, such as consistent environments and easy setup.