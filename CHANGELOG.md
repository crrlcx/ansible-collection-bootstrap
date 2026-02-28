# Changelog

All notable changes to the `crrlcx.bootstrap` Ansible collection will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [1.4.12] - 2026-02-28

### Changed

- Refactored `repositories` role: remove legacy repositories before adding new ones in DEB822 format.
- Standardized architecture to `amd64` in `debian-modern` task.

## [1.4.10] - 2026-02-27

### Changed

- Refactored `motd` role: updated README, streamlined variable definitions, fixed loop using `{{ item }}`.
- Removed non-existent `tee` package from `motd` defaults.
- Switched `motd` tasks to `ansible.builtin.package` module.

## [1.4.4] - 2026-02-27

### Changed

- Refactored `swap` role: streamlined README, updated defaults, reorganized task files.
- Updated README and removed unused environment variables in `dns`, `ntp`, `udev` task files.
- Updated `ca` role README.

### Removed

- Removed `systemd-swap` support and bundled deb package from `swap` role.

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

[1.4.12]: https://github.com/crrlcx/ansible-collection-bootstrap/compare/1.4.10...1.4.12
[1.4.10]: https://github.com/crrlcx/ansible-collection-bootstrap/compare/1.4.4...1.4.10
[1.4.4]: https://github.com/crrlcx/ansible-collection-bootstrap/compare/1.4.0...1.4.4
[1.4.0]: https://github.com/crrlcx/ansible-collection-bootstrap/compare/1.3.1...1.4.0
[1.3.1]: https://github.com/crrlcx/ansible-collection-bootstrap/compare/1.3.0...1.3.1
[1.3.0]: https://github.com/crrlcx/ansible-collection-bootstrap/compare/1.2.55...1.3.0
[1.2.55]: https://github.com/crrlcx/ansible-collection-bootstrap/compare/1.1.8...1.2.55
[1.1.8]: https://github.com/crrlcx/ansible-collection-bootstrap/compare/1.0.7...1.1.8
[1.0.7]: https://github.com/crrlcx/ansible-collection-bootstrap/compare/1.0.0...1.0.7
[1.0.0]: https://github.com/crrlcx/ansible-collection-bootstrap/releases/tag/1.0.0
