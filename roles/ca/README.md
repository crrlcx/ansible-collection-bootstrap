# About

Ansible role `ca` to install trusted CA certificates from URL or inline content.

## Requirements

- Debian or RedHat based OS

## Role variables

### Defaults

```yaml
bootstrap_ca: false

ca_dest: /usr/local/share/ca-certificates

ca_certificates: []
```

Each item in `ca_certificates` requires `name` and either `url` or `content`:

```yaml
ca_certificates:
  - name: my-root-ca
    url: https://example.com/ca.crt
  - name: internal-ca
    content: |
      -----BEGIN CERTIFICATE-----
      MIIFazCCA1OgAwIBAgIUE...
      -----END CERTIFICATE-----
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
    - role: crrlcx.bootstrap.ca
```

> **Note:** This role requires `become: true` at the play level.

## License

MIT
