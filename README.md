# ansible_kubectl_krew

[![Molecule Test](https://github.com/somaz94/ansible_kubectl_krew/actions/workflows/molecule-test.yml/badge.svg)](https://github.com/somaz94/ansible_kubectl_krew/actions/workflows/molecule-test.yml)
[![Release](https://github.com/somaz94/ansible_kubectl_krew/actions/workflows/release.yml/badge.svg)](https://github.com/somaz94/ansible_kubectl_krew/actions/workflows/release.yml)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-somaz94.ansible__kubectl__krew-blue.svg)](https://galaxy.ansible.com/ui/standalone/roles/somaz94/ansible_kubectl_krew/)

Ansible role to install kubectl and krew plugins.

<br/>

## Requirements

- Ansible 2.9 or higher
- Targeted OS: Debian/Ubuntu, RHEL/CentOS

<br/>

## Role Variables

The variables below can be modified in the `vars/main.yml` file as per your requirements:

- `home_user`: User for which the tooling setup should be applied.
- `krew_version`: Desired version of krew. Default: `v0.4.4`
- `krew_plugins`: List of krew plugins to be installed.

<br/>

## Dependencies

None.

<br/>

## Example Playbook

### Running Locally

#### 1. Setting Up the Variable File
Define the necessary variables in the `vars.yml` file:
```yaml
# vars.yml
home_user: "somaz"
krew_version: "v0.4.4"
krew_plugins:
  - "ctx"
  - "neat"
  - "ns"
  # more...
```
- For a comprehensive list of available krew plugins, visit the official [krew plugins directory](https://krew.sigs.k8s.io/plugins/).

#### 2. Creating the Playbook

Write the playbook in the `site.yml` file:
```yaml
# site.yml
---
- hosts: localhost
  become: yes
  vars_files:
    - ~/vars.yml
  roles:
    - somaz94.ansible_kubectl_krew
```

#### 3. Running the Playbook

Execute the playbook with the following command:
```bash
ansible-playbook site.yml
```

<br/>

### Running Remotely

#### 1. Setting Up the Variable File

Define the necessary variables in the `vars.yml` file:
```yaml
# vars.yml
home_user: "somaz"
krew_version: "v0.4.4"
krew_plugins:
  - "ctx"
  - "neat"
  - "ns"
  # more...
```

#### 2. Setting Up the Inventory File
Define the remote server information and connection details in the `inventory.ini` file:
```ini
# inventory.ini
[test_servers]
test-server ansible_ssh_user=somaz ansible_ssh_private_key_file=~/.ssh/id_rsa
```

#### 3. Creating the Playbook
Write the playbook in the `site.yml` file:
```yaml
# site.yml
---
- hosts: test_servers
  become: yes
  vars_files:
    - ~/vars.yml
  roles:
    - somaz94.ansible_kubectl_krew
```

#### 4. Running the Playbook
Execute the playbook with the following command:
```bash
ansible-playbook -i inventory.ini site.yml
```

<br/>

## Local Development

```bash
# Create virtual environment and install dependencies
make venv

# Run full molecule test
make test

# Run with specific distro
make test DISTRO=rockylinux9

# Run ansible-lint
make lint
```

<br/>

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

<br/>

## Author Information

- somaz94
- genius5711@gmail.com
- https://github.com/somaz94
