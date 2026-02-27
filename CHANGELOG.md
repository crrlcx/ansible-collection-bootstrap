# Changelog

All notable changes to the `crrlcx.bootstrap` Ansible collection will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [1.4.0] - 2026-02-27

### Added

- `repositories` role for APT repository management (legacy and DEB822 formats).
- This changelog file.

## [1.3.1] - 2022-11-16

### Changed

- Updated feature flags in bootstrap playbook.
- Miscellaneous improvements and fixes.

## [1.3.0] - 2022-10-13

### Added

- `hosts` role for hostname and `/etc/hosts` management.

## [1.2.55] - 2022-10-13

### Added

- `udev` role for udev rules management.

## [1.1.8] - 2022-10-12

### Added

- `dns` role for DNS resolver configuration.
- `ping.yml` playbook for connectivity testing.
- Feature flags in `bootstrap.yml` playbook (`bootstrap_hosts`, `bootstrap_sysctl`, etc.).

### Changed

- Renamed `timesyncd` role to `ntp`.
- Disabled IPv6 configuration by default.

## [1.0.7] - 2022-09-20

### Changed

- Documentation updates.
- CI linting improvements.
- Build ignore patterns for Galaxy packaging.

## [1.0.0] - 2022-09-20

### Added

- Initial release of the `crrlcx.bootstrap` collection.
- Roles: `bootstrap`, `ca`, `ntp`, `ssh`, `motd`, `sysctl`.
- Bootstrap playbook for orchestrating all roles.

[1.4.0]: https://github.com/crrlcx/ansible-collection-boostrap/compare/1.3.1...1.4.0
[1.3.1]: https://github.com/crrlcx/ansible-collection-boostrap/compare/1.3.0...1.3.1
[1.3.0]: https://github.com/crrlcx/ansible-collection-boostrap/compare/1.2.55...1.3.0
[1.2.55]: https://github.com/crrlcx/ansible-collection-boostrap/compare/1.1.8...1.2.55
[1.1.8]: https://github.com/crrlcx/ansible-collection-boostrap/compare/1.0.7...1.1.8
[1.0.7]: https://github.com/crrlcx/ansible-collection-boostrap/compare/1.0.0...1.0.7
[1.0.0]: https://github.com/crrlcx/ansible-collection-boostrap/releases/tag/1.0.0
