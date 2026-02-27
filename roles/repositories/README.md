# Repositories

Manages package repositories, including configuring internal Ubuntu/Debian mirror sources.

Uses legacy `apt_key`/`apt_repository` for older distributions (< 20) and modern `deb822_repository` for newer ones (>= 20).

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `bootstrap_repositories` | `false` | Enable repository management |
| `repositories_list` | `[]` | List of repository definitions |

Each item in `repositories_list` expects the following keys:

| Key | Description |
|---|---|
| `name` | Repository name (modern only) |
| `url` | Repository URL |
| `key` | GPG key — URL or local path |
| `suites` | Suites — string or list, e.g. `"noble"` (modern only) |
| `components` | Components — string or list, e.g. `"stable"` (modern only) |
| `architectures` | Architectures — string or list, e.g. `"amd64"` (modern only) |

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: crrlcx.boostrap.repositories
      vars:
        bootstrap_repositories: true
        repositories_list:
          - name: docker
            url: https://download.docker.com/linux/ubuntu
            key: https://download.docker.com/linux/ubuntu/gpg
            suites: noble
            components: stable
            architectures: amd64
          - name: grafana
            url: https://apt.grafana.com
            key: https://apt.grafana.com/gpg.key
            suites: stable
            components: main
            architectures: amd64
```

## Example `repositories_list` (group_vars)

Modern format (Ubuntu >= 20):

```yaml
repositories_list:
  - name: docker
    url: https://download.docker.com/linux/ubuntu
    key: https://download.docker.com/linux/ubuntu/gpg
    suites: noble
    components: stable
    architectures: amd64
  - name: grafana
    url: https://apt.grafana.com
    key: https://apt.grafana.com/gpg.key
    suites: stable
    components: main
    architectures: amd64
```

Legacy format (Ubuntu < 20):

```yaml
repositories_list:
  - url: "deb https://download.docker.com/linux/ubuntu bionic stable"
    key: https://download.docker.com/linux/ubuntu/gpg
  - url: "deb https://apt.grafana.com stable main"
    key: https://apt.grafana.com/gpg.key
```
