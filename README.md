# ansible-role-andscape-client

An [Ansible](https://www.ansible.com) role to configure [Canonical Landscape Client](https://landscape.canonical.com/) on Debian Based Systems.

## Requirements

Landscape SaaS Account or self-hosted Landscape Server.

## Role Variables

### Landscape SaaS

```yaml
---
# Landscape server self-hosted
landscape_client_server_self_hosted: false

# Landscape account name
landscape_client_account_name: account-name

# Landscape Server urls
landscape_client_server_ping_url: "http://landscape.canonical.com/ping"
landscape_client_server_url: "https://landscape.canonical.com/message-system"

# Landscape client data path
landscape_client_data_path: "/var/lib/landscape/client"

# Landscape client log level: debug, info, warning, error or critical
landscape_client_log_level: "info"

# Force landscape client to register
landscape_client_force_register: false
```

### Self-hosted

```yaml
---
# defaults file for ansible-role-andscape-client

# Landscape server
landscape_client_server: "{{ groups['landscape_server'][0] }}"

# Landscape server self-hosted
landscape_client_server_self_hosted: true

# Landscape account name
landscape_client_account_name: account-name

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
```

## Dependencies

None

## Example Playbook

```yaml
---
- name: Configure Landscape Client
  hosts: all
  vars:
    # dgibbs64.landscape-client
    landscape_client_account_name: landscape-account-name
    landscape_client_computer_title: "Computer Name"
    landscape_client_access_group: "access-group"
    landscape_client_tags: "web, db, apache"
  roles:
    - role: ansible-role-andscape-client
```

## License

MIT

## Author Information

Updated by: Daniel Gibbs

- [Daniel Gibbs](https://danielgibbs.co.uk)

Larry Smith Jr.

- [@mrlesmithjr](https://www.twitter.com/mrlesmithjr)
- [EverythingShouldBeVirtual](http://www.everythingshouldbevirtual.com)
- mrlesmithjr [at] gmail.com
