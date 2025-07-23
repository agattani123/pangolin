<details>
<summary>Relevant source files</summary>

The following files were used as context for generating this wiki page:

- [install/Makefile](https://github.com/agattani123/pangolin/blob/main/install/Makefile)
- [docker-compose.yml](https://github.com/agattani123/pangolin/blob/main/docker-compose.yml)
- [src/components/Header.tsx](https://github.com/agattani123/pangolin/blob/main/src/components/Header.tsx)
- [src/pages/index.tsx](https://github.com/agattani123/pangolin/blob/main/src/pages/index.tsx)
- [src/utils/api.ts](https://github.com/agattani123/pangolin/blob/main/src/utils/api.ts)
</details>

# Getting Started

## Introduction

Pangolin is a web application that provides a user-friendly interface for interacting with various backend services. This "Getting Started" guide covers the process of setting up and running the Pangolin application locally for development purposes. It explains the application's architecture, key components, and how they interact with each other.

Sources: [docker-compose.yml](), [src/components/Header.tsx](), [src/pages/index.tsx](), [src/utils/api.ts]()

## Application Architecture

Pangolin follows a client-server architecture, where the client-side is a Next.js application built with React and TypeScript, and the server-side consists of various backend services.

```mermaid
graph TD
    Client[Client<br>/Next.js App/]
    Server[Server<br>/Backend Services/]
    Client -- Requests --> Server
    Server -- Responses --> Client
```

Sources: [docker-compose.yml](), [src/components/Header.tsx](), [src/pages/index.tsx](), [src/utils/api.ts]()

### Client-side (Next.js App)

The client-side of Pangolin is a Next.js application built with React and TypeScript. It provides the user interface and handles user interactions, sending requests to the backend services and rendering the responses.

```mermaid
graph TD
    UI[User Interface]
    API[API Utilities]
    UI -- Interacts --> API
    API -- Requests --> Backend[Backend Services]
    Backend -- Responses --> API
    API -- Updates --> UI
```

Sources: [src/components/Header.tsx](), [src/pages/index.tsx](), [src/utils/api.ts]()

### Server-side (Backend Services)

The server-side of Pangolin consists of various backend services responsible for handling different functionalities. These services may include databases, APIs, and other microservices.

```mermaid
graph TD
    Backend[Backend Services]
    Database[Database]
    API[API]
    Microservice[Microservice]
    Backend --> Database
    Backend --> API
    Backend --> Microservice
```

Sources: [docker-compose.yml]()

## Development Setup

To set up the Pangolin application for local development, follow these steps:

1. **Clone the repository**
2. **Install dependencies**
3. **Configure environment variables**
4. **Start the development server**

```mermaid
sequenceDiagram
    participant Developer
    participant Terminal
    Developer->>Terminal: git clone <repository_url>
    Terminal-->>Developer: Repository cloned
    Developer->>Terminal: npm install
    Terminal-->>Developer: Dependencies installed
    Developer->>Terminal: Configure environment variables
    Terminal-->>Developer: Environment variables configured
    Developer->>Terminal: npm run dev
    Terminal-->>Developer: Development server started
```

Sources: [docker-compose.yml]()

## Docker Compose

Pangolin provides a Docker Compose configuration for running the application and its dependencies in a containerized environment. The `docker-compose.yml` file defines the services and their configurations.

```mermaid
graph TD
    Docker[Docker Compose]
    App[App Service]
    Database[Database Service]
    Docker --> App
    Docker --> Database
```

Sources: [docker-compose.yml]()

The `app` service in the `docker-compose.yml` file defines the configuration for the Pangolin application container, including:

- Build context and Dockerfile
- Container name
- Exposed ports
- Environment variables
- Mounted volumes for code changes
- Restart policy

```mermaid
graph TD
    App[App Service]
    Build[Build Context]
    Ports[Exposed Ports]
    Env[Environment Variables]
    Volumes[Mounted Volumes]
    Restart[Restart Policy]
    App --> Build
    App --> Ports
    App --> Env
    App --> Volumes
    App --> Restart
```

Sources: [docker-compose.yml]()

## Makefile

The `install/Makefile` provides various targets for building and managing the Pangolin application.

```mermaid
graph TD
    Makefile[Makefile]
    Build[Build Targets]
    Clean[Clean Targets]
    UpdateVersions[Update Versions]
    Makefile --> Build
    Makefile --> Clean
    Makefile --> UpdateVersions
```

Sources: [install/Makefile]()

The `go-build-release` target builds the Pangolin installer binary for Linux platforms (amd64 and arm64).

```mermaid
sequenceDiagram
    participant Makefile
    participant Go
    Makefile->>Go: CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o bin/installer_linux_amd64
    Go-->>Makefile: Binary built for Linux amd64
    Makefile->>Go: CGO_ENABLED=0 GOOS=linux GOARCH=arm64 go build -o bin/installer_linux_arm64
    Go-->>Makefile: Binary built for Linux arm64
```

Sources: [install/Makefile:3-4]()

The `update-versions` target fetches the latest versions of Pangolin, Gerbil, and Badger from their respective GitHub repositories and updates the corresponding version variables in the `main.go` file.

```mermaid
sequenceDiagram
    participant Makefile
    participant GitHub
    participant Sed
    Makefile->>GitHub: Fetch latest Pangolin version
    GitHub-->>Makefile: Pangolin version
    Makefile->>GitHub: Fetch latest Gerbil version
    GitHub-->>Makefile: Gerbil version
    Makefile->>GitHub: Fetch latest Badger version
    GitHub-->>Makefile: Badger version
    Makefile->>Sed: Update Pangolin version in main.go
    Sed-->>Makefile: Pangolin version updated
    Makefile->>Sed: Update Gerbil version in main.go
    Sed-->>Makefile: Gerbil version updated
    Makefile->>Sed: Update Badger version in main.go
    Sed-->>Makefile: Badger version updated
```

Sources: [install/Makefile:9-20]()

## Conclusion

This "Getting Started" guide provides an overview of the Pangolin application's architecture, development setup process, Docker Compose configuration, and the Makefile targets for building and managing the application. It covers the key components and their interactions, as well as the steps required to run the application locally for development purposes.

Sources: [install/Makefile](), [docker-compose.yml](), [src/components/Header.tsx](), [src/pages/index.tsx](), [src/utils/api.ts]()