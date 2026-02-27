# About

Ansible role `sysctl` create, update and apply settings with sysctl.
Saves to file, apply all settings in one time.

## Requirements

Linux with python as target.

## Role variables

### Defaults

```yaml
sysctl_file: /etc/sysctl.conf # file to save settings
sysctl_reload: true # apply option with sysctl -p
sysctl_set: false # check option with sysctl -w

sysctl_vars: { ... } # dict of configuration options
```

### Override

```yaml
sysctl_vars_override: {} # dict of configuration options for override default values
```

## Dependencies

None

## Example playbook

```yaml
- hosts: servers
  collections:
    - sage.bootstrap
  roles:
    - role: sage.bootstrap.sysctl
```

## License

MIT
