This Ansible role automates the installation and configuration of Docker on Debian-based systems. It includes support for Docker Compose and custom Docker network setups.

## Features

- Updates and upgrades all system packages.
- Installs necessary dependencies for Docker.
- Configures the Docker repository and adds the official GPG key.
- Installs Docker Engine, CLI, and plugins like Docker Compose.
- Creates a custom Docker network.
- Adds the specified user to the Docker group.
- Starts and enables Docker services.

## Requirements

- **Supported OS:** This role is designed to work on **Debian-based distributions** (e.g., Debian, Ubuntu). Other distributions are not officially supported.
- **Ansible Version:** Tested with Ansible 2.12 and higher.
- **Python Requirements:** Ensure `python3` and `pip` are installed on the target system.

## Role Variables

The following variables can be customized in `defaults/main.yml`:

| Variable                | Default Value                  | Description                                    |
|-------------------------|--------------------------------|------------------------------------------------|
| `docker_packages`       | See `defaults/main.yml`       | List of Docker packages to install.           |
| `required_packages`     | See `defaults/main.yml`       | System dependencies for Docker installation.  |
| `docker_network.name`   | `traefik`                    | Name of the custom Docker network.            |
| `docker_network.subnet` | `10.5.0.0/24`                | Subnet for the custom Docker network.         |
| `docker_network.gateway`| `10.5.0.1`                   | Gateway for the custom Docker network.        |

## Usage

### Basic Example

Include this role in your playbook:

```yaml
- hosts: all
  roles:
    - docker_role