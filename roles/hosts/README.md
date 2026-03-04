# About

Ansible role `hosts` to update hostname and /etc/hosts.
Also set the timezone for system

## Requirements

- Ubuntu/Debian

## Role variables

### Defaults

```yaml
---
## Hostname
hosts_hostname: "{{ inventory_hostname_short }}"
hosts_hostname_fqdn: "{{ inventory_hostname }}"

hosts_file_conditions: {}
```

### Example configuration

```yaml
---
hosts_file_conditions:
  cloudflare.dns: 1.1.1.1
```

## Dependencies

-

## Example playbook

```yaml
- hosts: servers
  collections:
    - crrlcx.bootstrap
  roles:
    - role: crrlcx.bootstrap.hosts
```

## License

MIT
