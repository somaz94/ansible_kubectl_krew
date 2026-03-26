# CLAUDE.md - ansible_kubectl_krew

Ansible role for installing kubectl, krew, and krew plugins on Linux systems.

## Project Structure

- **Language**: YAML (Ansible role)
- **Type**: Ansible Galaxy role (`somaz94.ansible_kubectl_krew`)
- Installs latest kubectl, krew plugin manager, configurable krew plugins
- Sets up bash completion, `k` alias, krew PATH
- Multi-distro: Ubuntu 22.04+, Debian 11+, Rocky Linux 9+, Fedora 40+

## Key Files

- `tasks/main.yml` — Installation logic (kubectl, krew, plugins)
- `defaults/main.yml` — Default variables (krew_plugins: ctx, neat, ns)
- `molecule/` — Molecule test scenarios

## Build & Test

```bash
make venv    # Create virtualenv + install deps
make test    # Run Molecule tests (default distro)
make lint    # Run ansible-lint
make clean   # Remove artifacts
```

## Usage

```bash
ansible-galaxy role install somaz94.ansible_kubectl_krew
ansible-playbook site.yml
```
