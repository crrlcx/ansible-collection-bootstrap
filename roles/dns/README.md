# About

Ansible role `dns` to update time and date via NTP with systemd-timesyncd service.
Also set the timezone for system

## Requirements

- Ubuntu/Debian
- SystemD

## Role variables

### Defaults

```yaml
---
# dns servers
dns_servers: []
dns_servers_fallback: []
dns_domains: []
```

### Example configuration

```yaml
---
# dns servers for AWS Cloud
dns_servers:
  - 10.32.0.2
dns_domains:
  - "eu-central-1.compute.internal"
```

## Dependencies

- systemd
- systemd-resolved

## Example playbook

```yaml
- hosts: servers
  collections:
    - sage.bootstrap
  roles:
    - role: sage.bootstrap.dns
```

## License

MIT
