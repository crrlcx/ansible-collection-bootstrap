# About

Ansible role `grub` to manage GRUB bootloader configuration
using `lineinfile` regex updates on `/etc/default/grub`.

## Requirements

- Debian-based OS
- GRUB bootloader

## Role variables

### Defaults

```yaml
bootstrap_grub: false

grub_lines:
  GRUB_CMDLINE_LINUX:
    - apparmor=1
    - security=apparmor
    - libata.force=noncq
    - scsi_mod.use_blk_mq=1
    - dm_mod.use_blk_mq=1
    - zswap.enabled=1
    - zswap.compressor=lz4
    - zswap.max_pool_percent=20
    - cpufreq.default_governor=performance
    - ipv6.disable=1
    - init=/bin/systemd
  GRUB_CMDLINE_LINUX_DEFAULT:
    - console=tty0
    - no_timer_check
    - nofb
    - nomodeset
    - gfxpayload=text
  GRUB_DEFAULT: 0
  GRUB_DISABLE_LINUX_UUID: "true"
  GRUB_DISABLE_OS_PROBER: "false"
  GRUB_DISABLE_RECOVERY: '"true"'
  GRUB_GFXMODE: 640x480
```

Each key in `grub_lines` maps to a line in `/etc/default/grub`.

Values can be:

- **list** — joined with spaces and wrapped in double quotes: `GRUB_CMDLINE_LINUX="arg1 arg2"`
- **scalar** — written as-is: `GRUB_DEFAULT=0`
- **quoted scalar** — preserved literally: `GRUB_DISABLE_RECOVERY='"true"'` → `GRUB_DISABLE_RECOVERY="true"`

### Override example

```yaml
grub_lines:
  GRUB_DEFAULT: 0
  GRUB_TIMEOUT: 5
  GRUB_TIMEOUT_STYLE: menu
  GRUB_CMDLINE_LINUX_DEFAULT:
    - quiet
    - splash
  GRUB_CMDLINE_LINUX:
    - panic=5
    - nomodeset
  GRUB_DISABLE_OS_PROBER: "false"
  GRUB_DISABLE_RECOVERY: '"true"'
  GRUB_SERIAL_COMMAND: '"serial --speed=115200 --unit=0 --word=8 --parity=0 --stop=1"'
```

## Dependencies

None.

## Example playbook

```yaml
- hosts: servers
  become: true
  collections:
    - crrlcx.bootstrap
  roles:
    - role: crrlcx.bootstrap.grub
```

> **Note:** This role requires `become: true` at the play level.

## License

MIT
