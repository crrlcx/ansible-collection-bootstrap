# About

Ansible role `inadyn` to manage dynamic DNS client configuration and systemd service.

## Requirements

- Ubuntu/Debian

## Role variables

### Defaults

```yaml
---
bootstrap_inadyn: false

# defaults file for inadyn
inadyn_period: 300
inadyn_user_agent: "Mozilla/5.0"
inadyn_allow_ipv6: false
inadyn_config_path: /etc/inadyn.conf
inadyn_providers: []

```

### Example configuration

```yaml
---
inadyn_allow_ipv6: false
inadyn_providers:
  - name: cloudflare.com
    index: 1
    hostname: "{{ inventory_hostname }}"
    username: "{{ cloudflare_email | d('changeme@change.me') }}"
    password: "{{ cloudflare_api_key | d('changeme') }}"
    ssl: true
```

## Dependencies

-

## Example playbook

```yaml
- hosts: servers
  collections:
    - crrlcx.bootstrap
  roles:
    - role: crrlcx.bootstrap.inadyn
```

## License

MIT
