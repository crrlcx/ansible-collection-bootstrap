# About

Ansible role `motd` to manage MOTD and issue banners via fastfetch, refreshed hourly by cron.

## Requirements

- fastfetch
- cron or systemd-cron
- MOTD support (Ubuntu/Debian)
- Issue support (Ubuntu/Debian)

## Role variables

### Defaults

```yaml
motd_packages: # list of packages to install
  - fastfetch

motd_cron_script: /etc/cron.hourly/motd # path to cron.hourly script

motd_issue_dir: /etc/issue.d     # directory for issue files
motd_dir: /etc/motd.d            # directory for motd files
motd_file: fastfetch             # output filename (motd_file for motd, motd_file.issue for issue)
```

## Dependencies

- fastfetch
- cron or systemd-cron

## Example playbook

```yaml
- hosts: servers
  collections:
    - crrlcx.bootstrap
  roles:
    - role: crrlcx.bootstrap.motd
```

## License

MIT
