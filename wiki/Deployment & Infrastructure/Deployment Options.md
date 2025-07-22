<details>
<summary>Relevant source files</summary>

The following files were used as context for generating this wiki page:

- [Dockerfile.dev](https://github.com/agattani123/pangolin/blob/main/Dockerfile.dev)
- [Dockerfile.pg](https://github.com/agattani123/pangolin/blob/main/Dockerfile.pg)
- [Dockerfile.sqlite](https://github.com/agattani123/pangolin/blob/main/Dockerfile.sqlite)
- [docker-compose.yml](https://github.com/agattani123/pangolin/blob/main/docker-compose.yml)
- [package.json](https://github.com/agattani123/pangolin/blob/main/package.json)
</details>

# Deployment Options

## Introduction

The provided source files outline various deployment options for the Pangolin project, a web application built with Node.js and Next.js. The deployment configurations cover different scenarios, including development, production with PostgreSQL, and production with SQLite databases.

The project utilizes Docker and Docker Compose to streamline the deployment process and ensure consistent environments across different setups. The deployment options are defined through Dockerfiles and a Docker Compose configuration file.
Sources: [Dockerfile.dev](), [Dockerfile.pg](), [Dockerfile.sqlite](), [docker-compose.yml]()

## Development Environment

The `Dockerfile.dev` defines the setup for the development environment. It is based on the `node:20-alpine` image and includes the following steps:

1. Set the working directory to `/app`.
2. Copy the `package.json` and `package-lock.json` files.
3. Install project dependencies using `npm ci`.
4. Copy the entire project source code.
5. Start the development server with hot reload using `npm run dev`.

The development environment is designed for local development and testing purposes. It mounts the source code directories as volumes, allowing for code changes to be reflected immediately without rebuilding the container.
Sources: [Dockerfile.dev]()

## Production Environment with PostgreSQL

The `Dockerfile.pg` defines the setup for the production environment using a PostgreSQL database. It consists of two stages: a builder stage and a runner stage.

### Builder Stage

1. Set the working directory to `/app`.
2. Copy the `package.json` and `package-lock.json` files.
3. Install project dependencies using `npm ci`.
4. Copy the entire project source code.
5. Generate the database schema and migrations using Drizzle-Kit.
6. Build the Next.js application and the CLI tool.

### Runner Stage

1. Set the working directory to `/app`.
2. Install `curl` for health checks.
3. Copy the `package.json` and `package-lock.json` files.
4. Install production dependencies using `npm ci --omit=dev`.
5. Copy the built Next.js application, CLI tool, and database initialization files from the builder stage.
6. Copy the `pangctl` CLI wrapper script.
7. Copy the `names.json` file for the database.
8. Copy the `public` directory.
9. Start the production server using `npm run start:pg`.

The production environment with PostgreSQL is optimized for deployment to a production server or cloud environment. It builds the application and packages all the necessary files into a single container image.
Sources: [Dockerfile.pg](), [package.json]()

## Production Environment with SQLite

The `Dockerfile.sqlite` defines the setup for the production environment using an SQLite database. It follows a similar structure to the PostgreSQL setup, with a builder stage and a runner stage.

### Builder Stage

1. Set the working directory to `/app`.
2. Copy the `package.json` and `package-lock.json` files.
3. Install project dependencies using `npm ci`.
4. Copy the entire project source code.
5. Generate the database schema and migrations using Drizzle-Kit for SQLite.
6. Build the Next.js application and the CLI tool.

### Runner Stage

1. Set the working directory to `/app`.
2. Install `curl` for health checks.
3. Copy the `package.json` and `package-lock.json` files.
4. Install production dependencies using `npm ci --omit=dev`.
5. Copy the built Next.js application, CLI tool, and database initialization files from the builder stage.
6. Copy the `pangctl` CLI wrapper script.
7. Copy the `names.json` file for the database.
8. Copy the `public` directory.
9. Start the production server using `npm run start:sqlite`.

The production environment with SQLite is similar to the PostgreSQL setup, but it uses an SQLite database instead. This option might be suitable for smaller deployments or scenarios where a lightweight database solution is preferred.
Sources: [Dockerfile.sqlite](), [package.json]()

## Docker Compose Configuration

The `docker-compose.yml` file defines a Docker Compose configuration for the development environment. It includes a single service called `app`.

```yaml
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile.dev
    container_name: dev_pangolin
    ports:
      - "3000:3000"
      - "3001:3001"
      - "3002:3002"
    environment:
      - NODE_ENV=development
      - ENVIRONMENT=dev
      - DB_TYPE=pg
    volumes:
      # Mount source code for hot reload
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
    restart: no
```

The `app` service is built using the `Dockerfile.dev` and is named `dev_pangolin`. It maps ports `3000`, `3001`, and `3002` from the container to the host machine. The service sets environment variables for `NODE_ENV`, `ENVIRONMENT`, and `DB_TYPE`.

Additionally, the configuration mounts various project directories and configuration files as volumes, allowing for code changes to be reflected immediately in the running container.
Sources: [docker-compose.yml]()

## Conclusion

The Pangolin project provides different deployment options tailored for development and production environments. The development environment leverages hot reloading and mounted volumes for efficient local development. The production environments are optimized for deployment, with separate configurations for PostgreSQL and SQLite databases. Docker and Docker Compose are used to streamline the deployment process and ensure consistent environments across different setups.