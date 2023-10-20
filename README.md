# Role Name


ansible_kubectl_krew

<br/>

## Requirements


- Ansible 2.9 or higher
- Targeted OS: Deiban/Ubuntu, RHEL/CentOS (For now)

<br/>

## Role Variables


The variables below can be modified in the `~/vars.yml` file as per your requirements:
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
```bash
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
```bash
# site.yml
---
- hosts: localhost
  become: yes
  vars_files:
    - ~/vars.yml
  roles:
    - somaz94.ansible-kubectl-krew
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
```bash
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
```bash
# inventory.ini
[test_servers]
test-server ansible_ssh_user=somaz ansible_ssh_private_key_file=/home/somaz/.ssh/id_rsa_somaz94
```

#### 3. Creating the Playbook
Write the playbook in the `site.yml` file:
```bash
# site.yml
---
- hosts: test_servers
- hosts: <hosts> # Remote Server
  become: yes
  vars_files:
    - ~/vars.yml
  roles:
    - somaz94.ansible-kubectl-krew
```

#### 4. Running the Playbook
Execute the playbook with the following command:
```bash
ansible-playbook -i inventory.ini site.yml
```

<br/>

## License


This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author Information


- somaz94
- genius5711@gmail.com
- https://github.com/somaz94
