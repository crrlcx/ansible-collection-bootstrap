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
  ds-pager.sage.tcsbank.ru: 10.213.196.45
  m1-pager.sage.tcsbank.ru: 10.212.193.29
```

## Dependencies

-

## Example playbook

```yaml
- hosts: servers
  collections:
    - sage.bootstrap
  roles:
    - role: sage.bootstrap.hosts
```

## License

MIT
