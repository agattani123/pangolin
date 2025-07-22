<details>
<summary>Relevant source files</summary>

The following file was used as context for generating this wiki page:

- [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

</details>

# Introduction

Pangolin is an open-source, self-hosted tunneled reverse proxy server designed to securely expose private resources on distributed networks to the internet. It acts as a central hub, connecting isolated networks, even those behind restrictive firewalls, through encrypted tunnels, enabling easy access to remote services without opening ports.

## Key Components

### Reverse Proxy Through WireGuard Tunnel

Pangolin allows you to expose private resources on your network without opening ports (firewall punching) by leveraging a secure and easy-to-configure private connectivity via a custom user space WireGuard client, [Newt](https://github.com/fosrl/newt). It also supports any other WireGuard client.

Key features of the reverse proxy include:

- Automated SSL certificates (HTTPS) via [LetsEncrypt](https://letsencrypt.org/).
- Support for HTTP/HTTPS and raw TCP/UDP services.
- Load balancing.
- Ability to extend functionality with existing [Traefik](https://github.com/traefik/traefik) plugins, such as [CrowdSec](https://plugins.traefik.io/plugins/6335346ca4caa9ddeffda116/crowdsec-bouncer-traefik-plugin) and [Geoblock](https://github.com/PascalMinder/geoblock).
  - Automatic installation and configuration of CrowdSec via Pangolin's installer script.
- Attach as many sites to the central server as desired.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md#reverse-proxy-through-wireguard-tunnel)

### Identity & Access Management

Pangolin provides a centralized authentication system using platform SSO, allowing users to manage a single login. It offers the following access control and authentication features:

- Define access control rules for IPs, IP ranges, and URL paths per resource.
- TOTP with backup codes for two-factor authentication.
- Create organizations, each with multiple sites, users, and roles.
- Role-based access control to manage resource access permissions.
- Additional authentication options:
  - Email whitelisting with one-time passcodes.
  - Temporary, self-destructing share links.
  - Resource-specific pin codes.
  - Resource-specific passwords.
  - Passkeys.
- External identity provider (IdP) support with OAuth2/OIDC, such as Authentik, Keycloak, Okta, and others.
  - Auto-provision users and roles from your IdP.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md#identity--access-management)

## Use Cases

Pangolin can be used in various scenarios, including:

- Managing access to internal apps by granting users access from anywhere using just a web browser, without requiring client software.
- Exposing and testing internal tools and dashboards like Grafana for developers and DevOps teams.
- Serving as a secure API gateway, acting as one application load balancer across multiple clouds and on-premises environments.
- Easily exposing IoT devices, edge servers, or Raspberry Pi to the internet for field equipment monitoring.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md#use-cases)

## Deployment Options

Pangolin offers several deployment options:

1. **Fully Self Hosted**: Host the full application on your own server or on the cloud with a VPS.
2. **Pangolin Cloud**: Easy-to-use with simple pay-as-you-go pricing, fully managed for you.
3. **Hybrid & High Availability**: Managed control plane with your infrastructure, where Fossorial manages the database and control plane, while you self-host a lightweight exit-node. Traffic flows through your infrastructure, and Fossorial coordinates failover between your nodes or to the Cloud when issues arise.
4. **Full Enterprise On-Premises**: For full distributed and enterprise deployments on your infrastructure, controlled by your team.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md#deployment-options)

## Project Development and Roadmap

The Pangolin project welcomes feature requests from the community, which can be added to the [discussion board](https://github.com/orgs/fosrl/discussions/categories/feature-requests).

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md#project-development--roadmap)

## Licensing

Pangolin is dual-licensed under the AGPL-3 and the Fossorial Commercial license. For inquiries about commercial licensing, please contact the team at [numbat@fossorial.io](mailto:numbat@fossorial.io).

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md#licensing)

## Contributions

Contributions to the Pangolin project are welcome. You can find issues marked with "help wanted" in the [Issues](https://github.com/fosrl/pangolin/issues?q=is%3Aissue%20state%3Aopen%20label%3A%22help%20wanted%22) section of the repository. Please refer to the [CONTRIBUTING](./CONTRIBUTING.md) file for guidelines and best practices.

Bug reports and other functional issues can be posted in the [Issues](https://github.com/fosrl/pangolin/issues) section of the repository.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md#contributions)

In summary, Pangolin is a secure gateway to private networks, providing a tunneled reverse proxy server with identity and access control features. It enables easy access to remote services without opening ports, while offering various deployment options and welcoming community contributions.