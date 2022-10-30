# landscape_client

An [Ansible](https://www.ansible.com) role to configure [Canonical Landscape Client](https://landscape.canonical.com/) on Ubuntu.

|GitHub|Quality|Downloads|Version|
|------|-------|---------|-------|
|[![[github](https://github.com/dgibbs64/ansible-role-landscape_client/workflows/Ansible%20Molecule/badge.svg)](https://img.shields.io/github/workflow/status/dgibbs64/ansible-role-landscape_client/Ansible%20Molecule?label=molecule&logo=ansible&style=flat-square)](https://github.com/dgibbs64/ansible-role-landscape_client/actions)|[![[quality](https://img.shields.io/ansible/quality/59356)](https://img.shields.io/ansible/quality/59356?logo=ansible&style=flat-square)](https://galaxy.ansible.com/dgibbs64/landscape_client)|[![[downloads](https://img.shields.io/ansible/role/d/59356)](https://img.shields.io/ansible/role/d/59356?color=EE0000&logo=ansible&style=flat-square)](https://galaxy.ansible.com/dgibbs64/landscape_client)|[![[Version](https://img.shields.io/github/release/dgibbs64/ansible-role-landscape_client.svg)](https://img.shields.io/github/v/release/dgibbs64/ansible-role-landscape_client?logo=github&style=flat-square)](https://github.com/dgibbs64/landscape_client/releases/)|
## Requirements

Landscape SaaS Account or self-hosted Landscape Server.

## Role Variables

```yaml
---
# defaults file for ansible-role-landscape_client

# Landscape server
landscape_client_server: "{{ groups['landscape_server'][0] }}"

# Landscape server self-hosted
landscape_client_server_self_hosted: false

# Landscape account name
landscape_client_account_name: account-name

# Landscape Client computer title
landscape_client_computer_title: "computer title"

# Landscape Client access group
landscape_client_access_group: "access-group"

# Landscape Client tags
landscape_client_tags: "tag1, tag2"

## Self-hosted only
# Server certificate on client that will be used
landscape_client_ssl_cert: "/etc/landscape/server.pem"
## Directory of the SSL public key on the primary app server.
landscape_client_server_ssl_cert: "/etc/ssl/certs/ssl-cert-snakeoil.pem"

# Landscape Server urls
landscape_client_server_ping_url: "http://landscape.canonical.com/ping"
landscape_client_server_url: "https://landscape.canonical.com/message-system"

# Landscape client data path
landscape_client_data_path: "/var/lib/landscape/client"

# Landscape client log level: debug, info, warning, error or critical
landscape_client_log_level: "info"

# Force landscape client to register
landscape_client_force_register: false

# Enable Landscape script execution
landscape_client_enable_script_users: false

# Users that can execute Landscape scripts
landscape_client_script_users: root
```

## Dependencies

None

## Example Playbook

### Landscape SaaS

```yaml
---
- name: "Configure Landscape Client"
  hosts: all
  vars:
    landscape_client_account_name: landscape-account-name
    landscape_client_computer_title: "Computer Title"
    landscape_client_access_group: "access-group"
    landscape_client_tags: "web, db, apache"
  roles:
    - role: dgibbs64.landscape_client
```

### Self-hosted

```yaml
---
- name: "Configure Landscape Client"
  hosts: all
  vars:
    landscape_client_server: "{{ groups['landscape_server'][0] }}"
    landscape_client_account_name: landscape-account-name
    landscape_client_computer_title: "Computer Title"
    landscape_client_access_group: "access-group"
    landscape_client_tags: "web, db, apache"
    landscape_client_server_ping_url: "http://landscape.example.com/ping"
    landscape_client_server_url: "https://landscape.example.com/message-system"
  roles:
    - role: dgibbs64.landscape_client
```

## License

MIT

## Author Information

Updated by: Daniel Gibbs

- [Daniel Gibbs](https://danielgibbs.co.uk)

Original by Larry Smith Jr.

- [@mrlesmithjr](https://www.twitter.com/mrlesmithjr)
- [EverythingShouldBeVirtual](http://www.everythingshouldbevirtual.com)
- mrlesmithjr [at] gmail.com
