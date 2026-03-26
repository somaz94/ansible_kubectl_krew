# Ansible Kubectl Krew

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-somaz94.ansible__kubectl__krew-blue.svg)](https://galaxy.ansible.com/ui/standalone/roles/somaz94/ansible_kubectl_krew/)
[![Molecule Test](https://github.com/somaz94/ansible_kubectl_krew/actions/workflows/molecule-test.yml/badge.svg)](https://github.com/somaz94/ansible_kubectl_krew/actions/workflows/molecule-test.yml)
[![Release](https://github.com/somaz94/ansible_kubectl_krew/actions/workflows/release.yml/badge.svg)](https://github.com/somaz94/ansible_kubectl_krew/actions/workflows/release.yml)
[![Galaxy Publish](https://github.com/somaz94/ansible_kubectl_krew/actions/workflows/galaxy-publish.yml/badge.svg)](https://github.com/somaz94/ansible_kubectl_krew/actions/workflows/galaxy-publish.yml)
[![GitHub tag](https://img.shields.io/github/v/tag/somaz94/ansible_kubectl_krew)](https://github.com/somaz94/ansible_kubectl_krew/tags)
[![License](https://img.shields.io/github/license/somaz94/ansible_kubectl_krew)](LICENSE)

An Ansible role for installing kubectl and krew plugins on Unix/Linux systems.

<br/>

## Requirements

- Ansible 2.9+
- Supported OS: Ubuntu 22.04+, Debian 11+, Rocky Linux 9+, Fedora 40+

<br/>

## Installation

```bash
ansible-galaxy role install somaz94.ansible_kubectl_krew
```

<br/>

## Role Variables

<br/>

### Defined in `defaults/main.yml`:

| Variable | Description | Default |
|----------|-------------|---------|
| `home_user` | Target user for kubectl/krew setup (required) | `""` |
| `krew_plugins` | List of krew plugins to install | `[ctx, neat, ns]` |

> **Note:** kubectl and krew are always installed as the latest version automatically.

<br/>

For a comprehensive list of available krew plugins, visit the official [krew plugins directory](https://krew.sigs.k8s.io/plugins/).

<br/>

## Usage

<br/>

### Variables

```yaml
# vars.yml
home_user: "your-username"
krew_plugins:
  - "ctx"
  - "neat"
  - "ns"
  # more...
```

<br/>

### Playbook

```yaml
# site.yml
---
- hosts: localhost
  become: true
  vars_files:
    - vars.yml
  roles:
    - somaz94.ansible_kubectl_krew
```

```bash
ansible-playbook site.yml
```

<br/>

### Running Remotely

```ini
# inventory.ini
[servers]
my-server ansible_ssh_user=somaz ansible_ssh_private_key_file=~/.ssh/id_rsa
```

```yaml
# site.yml
---
- hosts: servers
  become: true
  vars_files:
    - vars.yml
  roles:
    - somaz94.ansible_kubectl_krew
```

```bash
ansible-playbook -i inventory.ini site.yml
```

<br/>

## Development

<br/>

### Prerequisites

- Python 3.x
- Docker (for Molecule testing)

<br/>

### Quick Start

```bash
make venv                          # Create venv and install dependencies
make test                          # Full molecule test (default: ubuntu2204)
make test DISTRO=ubuntu2404        # Test with Ubuntu 24.04
make test DISTRO=debian12          # Test with Debian 12
make test DISTRO=rockylinux9       # Test with Rocky Linux 9
make converge                      # Apply role only
make verify                        # Run verification only
make destroy                       # Destroy test instances
make lint                          # Run ansible-lint
make clean                         # Remove venv and build artifacts
```

<br/>

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
