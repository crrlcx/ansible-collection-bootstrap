# About

Ansible role `udev` to create Udev rules for network and block devices.

## Requirements

- Ubuntu/Debian
- ethtool
- hdparm
- util-linux

## Role variables

### Defaults

```yaml
---
udev_io_queue_scheduler_nvme: "{% if ansible_kernel is version('5.0', '>') %}none{% else %}noop{% endif %}"
udev_io_queue_scheduler_ssd: "{% if ansible_kernel is version('5.0', '>') %}kyber{% else %}noop{% endif %}"
udev_io_queue_scheduler_hdd: "{% if ansible_kernel is version('5.0', '>') %}kyber{% else %}noop{% endif %}"
```

## Dependencies

- udev

## Example playbook

```yaml
- hosts: servers
  collections:
    - sage.bootstrap
  roles:
    - role: sage.bootstrap.udev
```

## License

MIT
