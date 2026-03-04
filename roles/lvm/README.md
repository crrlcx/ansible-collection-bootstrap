# ansible-manage-lvm

Ansible role to manage LVM Groups/Logical Volumes.

> NOTE: Can be used to create, extend or resize LVM Groups and volumes.

## Requirements

Devices/disks to be members of the LVM setup **must be** identified prior to
using this role.

## Role Variables

[defaults/main.yml](defaults/main.yml)

## Dependencies

None

## Example Playbook

```yaml
---
- hosts: test-nodes
  vars:
    lvm_groups:
      - vgname: test-vg
        disks:
          - /dev/sdb
          - /dev/sdc
        create: true
        lvnames:
          - lvname: test_1
            size: 5g
            create: true
            force: true
            filesystem: ext4
            mount: true
            mntp: /mnt/test_1
          - lvname: test_2
            size: 10g
            create: true
            force: false
            filesystem: ext4
            mount: true
            mntp: /mnt/test_2
    manage_lvm: true
  tasks:
    - name: Include lvm
      include_role:
        name: ansible-manage-lvm
```

## License

MIT

## Author Information

Larry Smith Jr.

- [@mrlesmithjr](https://twitter.com/mrlesmithjr)
- [mrlesmithjr@gmail.com](mailto:mrlesmithjr@gmail.com)
- [http://everythingshouldbevirtual.com](http://everythingshouldbevirtual.com)
