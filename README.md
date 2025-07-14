# Nhost Self-Hosted in Coder Workspace

This project provides a self-hosted deployment of the Nhost backend platform, designed to run seamlessly within a [Coder](https://coder.com/) workspace environment provisioned via Terraform.

## Overview

Nhost is an open-source backend-as-a-service (BaaS) that provides instant APIs, authentication, storage, and serverless functions. This setup allows you to run Nhost locally or in a cloud-based Coder workspace for development and testing.

## Features

- Self-hosted Nhost stack (Hasura, Postgres, Auth, Storage, etc.)
- Easy local development and testing
- Ready for use in Coder remote development environments
- Pre-configured with persistent storage and workspace-specific settings
- Access to Nhost and related services via secure subdomains in the Coder dashboard
- VS Code (browser-based) and code-server available out of the box

## Workspace Features

- **Automatic App URLs:** All Nhost services (Hasura, Auth, Storage, etc.) are exposed as apps in the Coder dashboard with their own subdomains for easy access.
- **Persistent Storage:** Your home directory and workspace files are stored on a persistent volume.
- **VS Code in Browser:** Access a full-featured VS Code environment directly from your browser.
- **Pre-installed Tools:** Docker, Docker Compose, Git, and other developer tools are available by default.

## Getting Started

### Prerequisites

- A running [Coder workspace](https://coder.com/docs/v2/latest/workspaces/) provisioned with the provided `main.tf` (Terraform)
- [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/) are pre-installed in the workspace

### Setup

1. **Clone this repository inside your Coder workspace:**
   ```sh
   git clone https://github.com/jovermier/coder-nhost-self-hosted.git
   cd nhost-self-hosted
   ```
2. **Start the Nhost stack:**
   ```sh
   docker compose up -d
   ```
3. **Access the services:**
   - Open the Coder dashboard and use the provided app links (subdomains) for each Nhost service (e.g., Hasura Console, Auth, Storage, MailHog, etc.).
   - Example URLs will be listed in the dashboard; you do not need to manually forward ports.

### Stopping the Stack

```sh
docker compose down
```

## Customization

- Edit the `docker-compose.yml` file to adjust service configurations, ports, or environment variables as needed.
- You can mount volumes or add custom scripts for migrations and seed data.

## Notes

- This setup is intended for development and testing only. For production, review Nhost and Docker security best practices.
- All service URLs are managed by Coder and accessible via the dashboard; no manual port forwarding is required.
- Workspace resources (CPU, memory, disk) can be configured at creation time via the Coder UI or Terraform parameters.
- If you need additional tools or extensions, use the VS Code Extensions marketplace or update the Terraform module.

## Resources

- [Nhost Documentation](https://docs.nhost.io/)
- [Coder Documentation](https://coder.com/docs/)

## License

MIT
