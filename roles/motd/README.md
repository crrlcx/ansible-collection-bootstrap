# About

Ansible role `motd` to manage MOTD and issue banners via fastfetch, refreshed hourly by cron.

## Requirements

- Ubuntu/Debian
- fastfetch

## Role variables

### Defaults

```yaml
motd_packages: # list of packages to install
  - fastfetch

motd_cron_script: /etc/cron.hourly/motd # path to cron.hourly script

motd_issue_dir: /etc/issue.d     # directory for issue files
motd_issue_file: "{{ motd_issue_dir }}/fastfetch.issue"

motd_motd_dir: /etc/motd.d       # directory for motd files
motd_motd_file: "{{ motd_motd_dir }}/fastfetch"
```

## Dependencies

- fastfetch
- cron

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
