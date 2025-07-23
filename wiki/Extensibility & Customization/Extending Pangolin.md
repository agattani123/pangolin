<details>
<summary>Relevant source files</summary>

The following files were used as context for generating this wiki page:

- [install/config/crowdsec/acquis.d/appsec.yaml](https://github.com/agattani123/pangolin/blob/main/install/config/crowdsec/acquis.d/appsec.yaml)
- [install/config/crowdsec/acquis.d/traefik.yaml](https://github.com/agattani123/pangolin/blob/main/install/config/crowdsec/acquis.d/traefik.yaml)
- [server/middlewares/integration/index.ts](https://github.com/agattani123/pangolin/blob/main/server/middlewares/integration/index.ts)
- [server/middlewares/integration/verifyApiKey.ts](https://github.com/agattani123/pangolin/blob/main/server/middlewares/integration/verifyApiKey.ts)
- [server/middlewares/integration/verifyApiKeyOrgAccess.ts](https://github.com/agattani123/pangolin/blob/main/server/middlewares/integration/verifyApiKeyOrgAccess.ts)

</details>

# Extending Pangolin

## Introduction

Pangolin is a security project that integrates various components to provide comprehensive protection and monitoring capabilities. This wiki page focuses on the process of extending Pangolin's functionality by incorporating additional security components and configuring them to work seamlessly with the existing system.

The primary components covered in this documentation are AppSec and Traefik, which are configured through the `acquis.d` directory in the `crowdsec` configuration. Additionally, the `server/middlewares/integration` directory contains middleware functions that handle API key verification and access control for different resources and actions within the Pangolin system.

## AppSec Integration

AppSec (Application Security) is a security component designed to monitor and protect web applications from various threats, such as SQL injection, cross-site scripting (XSS), and other common vulnerabilities.

### AppSec Configuration

The AppSec component is configured through the `appsec.yaml` file located in the `install/config/crowdsec/acquis.d` directory. This file defines the following settings:

```yaml
listen_addr: 0.0.0.0:7422
appsec_config: crowdsecurity/appsec-default
name: myAppSecComponent
source: appsec
labels:
  type: appsec
```

- `listen_addr`: The IP address and port on which AppSec listens for incoming connections.
- `appsec_config`: The default configuration file for AppSec.
- `name`: The name assigned to the AppSec component.
- `source`: The source identifier for AppSec.
- `labels`: Additional labels or tags associated with the AppSec component.

Sources: [install/config/crowdsec/acquis.d/appsec.yaml](https://github.com/agattani123/pangolin/blob/main/install/config/crowdsec/acquis.d/appsec.yaml)

## Traefik Integration

Traefik is a modern HTTP reverse proxy and load balancer that can be used to route incoming requests to various services and applications within the Pangolin system.

### Traefik Configuration

The Traefik component is configured through the `traefik.yaml` file located in the `install/config/crowdsec/acquis.d` directory. This file defines the following settings:

```yaml
poll_without_inotify: false
filenames:
  - /var/log/traefik/*.log
labels:
  type: traefik
```

- `poll_without_inotify`: A boolean flag that determines whether Traefik should poll for log file changes without using inotify.
- `filenames`: A list of log file paths that Traefik should monitor.
- `labels`: Additional labels or tags associated with the Traefik component.

Sources: [install/config/crowdsec/acquis.d/traefik.yaml](https://github.com/agattani123/pangolin/blob/main/install/config/crowdsec/acquis.d/traefik.yaml)

## API Key Verification and Access Control

The `server/middlewares/integration` directory contains a set of middleware functions that handle API key verification and access control for various resources and actions within the Pangolin system.

### Middleware Functions

The following middleware functions are exported from the `index.ts` file:

| Function | Description |
| --- | --- |
| `verifyApiKey` | Verifies the validity of an API key. |
| `verifyApiKeyOrgAccess` | Verifies if an API key has access to a specific organization. |
| `verifyApiKeyHasAction` | Verifies if an API key has permission to perform a specific action. |
| `verifyApiKeySiteAccess` | Verifies if an API key has access to a specific site. |
| `verifyApiKeyResourceAccess` | Verifies if an API key has access to a specific resource. |
| `verifyApiKeyTargetAccess` | Verifies if an API key has access to a specific target. |
| `verifyApiKeyRoleAccess` | Verifies if an API key has access to a specific role. |
| `verifyApiKeyUserAccess` | Verifies if an API key has access to a specific user. |
| `verifyApiKeySetResourceUsers` | Verifies if an API key can set resource users. |
| `verifyAccessTokenAccess` | Verifies if an access token has access to a specific resource. |
| `verifyApiKeyIsRoot` | Verifies if an API key has root access. |
| `verifyApiKeyApiKeyAccess` | Verifies if an API key has access to another API key. |

Sources: [server/middlewares/integration/index.ts](https://github.com/agattani123/pangolin/blob/main/server/middlewares/integration/index.ts)

Each of these middleware functions likely implements specific logic to verify the API key's permissions and access rights based on the requested resource, action, or target. However, the implementation details of these functions are not provided in the given source files.

## Conclusion

Extending Pangolin involves integrating additional security components, such as AppSec and Traefik, and configuring them through the `acquis.d` directory in the `crowdsec` configuration. The `server/middlewares/integration` directory provides a set of middleware functions for API key verification and access control, ensuring secure and authorized access to various resources and actions within the Pangolin system.

By following the configurations outlined in this documentation and leveraging the provided middleware functions, developers can enhance Pangolin's capabilities and tailor it to meet specific security requirements.