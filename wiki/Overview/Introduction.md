<details>
<summary>Relevant source files</summary>

The following file was used as context for generating this wiki page:

- [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

</details>

# Introduction

Pangolin is an open-source, self-hosted tunneled reverse proxy server designed to securely expose private resources on distributed networks. It acts as a central hub, connecting isolated networks, even those behind restrictive firewalls, through encrypted tunnels, enabling easy access to remote services without opening ports. Pangolin provides a secure gateway to your private networks, allowing you to access anything from anywhere.

## Key Features

### Reverse Proxy Through WireGuard Tunnel

Pangolin enables you to expose private resources on your network without opening ports (firewall punching). It provides secure and easy-to-configure private connectivity via a custom user space WireGuard client, [Newt](https://github.com/fosrl/newt). Pangolin also supports any WireGuard client out of the box.

Key features of the reverse proxy include:

- Automated SSL certificates (HTTPS) via [LetsEncrypt](https://letsencrypt.org/).
- Support for HTTP/HTTPS and raw TCP/UDP services.
- Load balancing capabilities.
- Ability to extend functionality with existing [Traefik](https://github.com/traefik/traefik) plugins, such as [CrowdSec](https://plugins.traefik.io/plugins/6335346ca4caa9ddeffda116/crowdsec-bouncer-traefik-plugin) and [Geoblock](https://github.com/PascalMinder/geoblock).
  - Pangolin's installer script can automatically install and configure CrowdSec.
- Attach as many sites to the central server as desired.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

### Identity & Access Management

Pangolin provides a centralized authentication system using platform SSO, allowing users to manage a single login. It offers the following identity and access management features:

- Define access control rules for IPs, IP ranges, and URL paths per resource.
- TOTP (Time-based One-Time Password) with backup codes for two-factor authentication.
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

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

## Use Cases

Pangolin can be utilized in various scenarios, including:

1. **Manage Access to Internal Apps**: Grant users access to your apps from anywhere using just a web browser, without the need for client software.
2. **Developers and DevOps**: Expose and test internal tools and dashboards like Grafana, bringing localhost or private IPs online for easy access.
3. **Secure API Gateway**: Pangolin can serve as a single application load balancer across multiple clouds and on-premises environments.
4. **IoT and Edge Devices**: Easily expose IoT devices, edge servers, or Raspberry Pi to the internet for field equipment monitoring.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

## Deployment Options

Pangolin offers several deployment options:

### Fully Self Hosted

You can host the full application on your own server or on a cloud VPS (Virtual Private Server). The [documentation](https://docs.fossorial.io/Getting%20Started/quick-install) provides guidance on getting started with self-hosting.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

### Pangolin Cloud

Pangolin Cloud is an easy-to-use option with simple pay-as-you-go pricing. It provides everything you get with the self-hosted version, but fully managed for you. You can check it out at [pangolin.fossorial.io/auth/signup](https://pangolin.fossorial.io/auth/signup).

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

### Hybrid & High Availability

In the hybrid and high availability deployment model, Pangolin manages the control plane and database, while you self-host a lightweight exit-node. Traffic flows through your infrastructure, and Pangolin coordinates failover between your nodes or to the Cloud when issues arise.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

### Full Enterprise On-Premises

For full distributed and enterprise deployments on your infrastructure, controlled by your team, you can contact Pangolin for more information.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

## Project Development and Roadmap

Pangolin welcomes feature requests from users, which can be added to the [discussion board](https://github.com/orgs/fosrl/discussions/categories/feature-requests).

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

## Licensing

Pangolin is dual-licensed under the AGPL-3 and the Fossorial Commercial license. For inquiries about commercial licensing, you can contact the Pangolin team at [numbat@fossorial.io](mailto:numbat@fossorial.io).

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

## Contributions

Pangolin welcomes contributions from the community. If you're looking for something to contribute, you can check the issues marked with [help wanted](https://github.com/fosrl/pangolin/issues?q=is%3Aissue%20state%3Aopen%20label%3A%22help%20wanted%22). The [CONTRIBUTING](./CONTRIBUTING.md) file in the repository provides guidelines and best practices for contributing.

Bug reports and other functional issues can be posted in the [Issues](https://github.com/fosrl/pangolin/issues) section of the repository.

Sources: [README.md](https://github.com/agattani123/pangolin/blob/main/README.md)

In summary, Pangolin is a powerful and secure tunneled reverse proxy server that provides a gateway to your private networks, enabling easy access to remote services from anywhere. With its comprehensive identity and access management features, deployment flexibility, and active community development, Pangolin offers a robust solution for securely exposing private resources on distributed networks.