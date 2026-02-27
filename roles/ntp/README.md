# About

Ansible role `ntp` to update time and date via NTP with systemd-timesyncd service.
Also set the timezone for system

## Requirements

- Ubuntu/Debian
- SystemD

## Role variables

### Defaults

```yaml
ntp_servers: # list of NTP servers
  - time.google.com
ntp_fallback_servers: # list of NTP fallback servers
  - ntp.ubuntu.com
  - 0.ru.pool.ntp.org
  - 1.ru.pool.ntp.org
  - 2.ru.pool.ntp.org
  - 3.ru.pool.ntp.org

ntp_root_distance_max_sec: 5
ntp_poll_interval_min_sec: 32
ntp_poll_interval_max_sec: 2048

timezone: "Etc/UTC" # text name of TimeZone
```

## Dependencies

- systemd
- systemd-timesyncd
- tzdata

## Example playbook

```yaml
- hosts: servers
  collections:
    - sage.bootstrap
  roles:
    - role: sage.bootstrap.ntp
```

## License

MIT
