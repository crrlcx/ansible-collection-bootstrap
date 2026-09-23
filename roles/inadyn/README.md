# About

Ansible role `inadyn` manages the Inadyn dynamic DNS client on Debian/Ubuntu systems.
It installs the package, renders `/etc/inadyn.conf`, removes the obsolete `--background` option from the init script when present, and ensures the daemon is enabled and restarted as needed.

## Requirements

- Debian or Ubuntu
- `ansible.builtin` standard modules only
- `inadyn` package available from the configured apt repository

## Role variables

### Defaults

```yaml
---
bootstrap_inadyn: false

inadyn_config_path: /etc/inadyn.conf
inadyn_period: 600
inadyn_forced_update: 2592000
inadyn_secure_ssl: true
inadyn_user_agent: "Mozilla/5.0"
inadyn_allow_ipv6: false
inadyn_providers: []
```

### Provider entries

Each item in `inadyn_providers` is rendered into a provider block in the configuration file.
The template supports the common Inadyn keys, including provider type and DDNS response fields.

```yaml
inadyn_providers:
  - type: provider
    name: cloudflare.com
    index: 1
    username: "{{ cloudflare_email | d('changeme@change.me') }}"
    password: "{{ cloudflare_api_key | d('changeme') }}"
    hostname: "{{ inventory_hostname }}"
    ssl: true
    checkip-server: "checkip.amazonaws.com"
    ddns-server: "https://api.cloudflare.com/client/v4/"
    ddns-response: "good"
```

Common fields:

- `type`: provider type used as the first token in the config block (provider or custom)
- `name`: provider name
- `index`: optional provider index, rendered as `name:index`
- `username`, `password`, `hostname`: credentials and target hostname
- `checkip_server`, `checkip_ssl`, `checkip_path`, `checkip_command`: optional check IP settings
- `ssl`, `user_agent`, `ttl`, `proxied`, `ddns_server`, `ddns_path`, `ddns_response`: provider-specific options

## Example playbook

```yaml
- hosts: servers
  collections:
    - crrlcx.bootstrap
  roles:
    - role: crrlcx.bootstrap.inadyn
```

An example inventory/vars file:

```yaml
bootstrap_inadyn: true
inadyn_allow_ipv6: false
inadyn_providers:
  - type: provider
    name: cloudflare.com
    index: 1
    username: "{{ cloudflare_email }}"
    password: "{{ cloudflare_api_key }}"
    hostname: "{{ inventory_hostname }}"
    ssl: true
    ddns-server: "https://api.cloudflare.com/client/v4/"
    ddns-response: "good"
```

## License

MIT
