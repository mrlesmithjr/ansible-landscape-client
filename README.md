<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [ansible-landscape-client](#ansible-landscape-client)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Dependencies](#dependencies)
  - [Example Playbook](#example-playbook)
  - [License](#license)
  - [Author Information](#author-information)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# ansible-landscape-client

An [Ansible](https://www.ansible.com) role to configure [Canonical Landscape Client](https://landscape.canonical.com/) on Debian Based Systems

## Requirements

A fully configured self-hosted or SaaS Landscape Server.

## Role Variables

```yaml
---
# defaults file for ansible-landscape-client

# Landscape server
landscape_client_server: "{{ groups['landscape_app'][0] }}"

# Landscape server self-hosted
landscape_client_server_on_prem: false
# Landscape account name
landscape_client_account_name: standalone
## On-prem only
# Server certificate on client that will be used
landscape_client_ssl_cert: '/etc/landscape/server.pem'
## Directory of the SSL public key on the primary app server.
landscape_client_server_ssl_cert: '/etc/ssl/certs/ssl-cert-snakeoil.pem'

# Landscape Server urls
landscape_client_server_ping_url: 'http://landscape.canonical.com/ping'
landscape_client_server_url: 'https://landscape.canonical.com/message-system'

# Landscape client data path
landscape_client_data_path: '/var/lib/landscape/client'

# Landscape client log level: debug, info, warning, error or critical
landscape_client_log_level: 'info'

# Force landscape client to register
landscape_client_force_register: false
```

## Dependencies

None

## Example Playbook

```yaml
---

- name: Configure Landscape Client
  hosts: all
  vars:
    # mrlesmithjr.landscape-client
    landscape_client_account_name: landscape-account-name
    landscape_client_computer_title: "Compuster Title"
    landscape_client_access_group: "access-group"
    landscape_client_tags: "web, db, apache"
  roles:
    - role: ansible-landscape-client
```

## License

MIT

## Author Information
Modified by: Daniel Gibbs


Larry Smith Jr.

-   [@mrlesmithjr](https://www.twitter.com/mrlesmithjr)
-   [EverythingShouldBeVirtual](http://www.everythingshouldbevirtual.com)
-   mrlesmithjr [at] gmail.com
