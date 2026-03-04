# Swap

Creates, resizes, or removes a swapfile based on toggle variables.

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `bootstrap_swap` | `false` | Include this role in the play |
| `swap_file_enabled` | `false` | Toggle: `true` creates swapfile, `false` removes it |
| `swap_file_path` | `/swapfile` | Path to the swapfile |
| `swap_file_size` | `2G` | Swapfile size (`512M`, `2G`, `4G`, etc.) |

## Example Playbook

Create a 4G swapfile:

```yaml
- hosts: all
  roles:
    - role: crrlcx.boostrap.swap
      vars:
        bootstrap_swap: true
        swap_file_enabled: true
        swap_file_size: 4G
```

Remove the swapfile:

```yaml
- hosts: all
  roles:
    - role: crrlcx.boostrap.swap
      vars:
        bootstrap_swap: true
        swap_file_enabled: false
```

## Dependencies

- `ansible.posix`

## License

MIT
