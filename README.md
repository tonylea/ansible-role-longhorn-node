# longhorn_node

Prepares a k3s node for Longhorn.
On every node it:

- Installs Longhorn's prerequisites: `open-iscsi` with `iscsid` running, and `nfs-common`.
- Loads the `dm_crypt` module now and at every boot.

Longhorn's manager runs on every node and won't start without these, and a node needs them to attach Longhorn volumes.

On a node that stores Longhorn data (`longhorn_node_data_disk: true`, the default) it also:

- Gives Longhorn its own ext4 storage, mounted at `/var/lib/longhorn` by UUID.
- Adds a k3s config drop-in so the node registers with the label `node.longhorn.io/create-default-disk=true`.

Longhorn's storage is one of two kinds:

- By default, a partition after root.
  The role grows the root partition to 32GiB, and its filesystem with it, then gives Longhorn the rest of the disk as a new partition right after root.
  It only grows root, never shrinks it.
  The disk is found from where `/` is mounted, so the role works on SATA/USB (`sda`) and NVMe disks alike.
  Run it before anything that installs packages on a freshly imaged node, whose root partition is still the image's small size.
- With `longhorn_node_whole_disk` set, a whole disk, such as a VM's second virtual disk.
  The role formats the disk itself, with no partition table, and leaves root alone.
  It stops if the disk has partitions, so it never formats the root disk or one holding other data.

k3s only applies node labels when a node first registers, so run this role before k3s is installed.

Tested on Debian trixie (Raspberry Pi OS, and Debian's generic cloud image with a whole disk).

## Variables

| Variable | Default |
| --- | --- |
| `longhorn_node_data_disk` | `true` |
| `longhorn_node_root_size_gib` | `32` |
| `longhorn_node_data_path` | `/var/lib/longhorn` |
| `longhorn_node_whole_disk` | `""`: a partition after root |
| `longhorn_node_root_device` | the device mounted at `/` |

## Requirements

The `ansible.posix` and `community.general` collections, pinned in `requirements.yml`.

## Usage

```yaml
- hosts: k3s_cluster
  become: true
  roles:
    - longhorn_node
```

## Development

Tests cover both kinds of storage, each in its own Debian trixie container running systemd, on a real disk: a sparse file on a loop device.
One disk is laid out like a freshly imaged Pi OS SSD; the other is empty, like a VM's second disk.
They check the partition and filesystem sizes, the mount and its `fstab` entry, `iscsid`, `dm_crypt` and the k3s drop-in, and that the role refuses to format a disk with partitions whole.

```sh
pip install -r requirements-test.txt
molecule test
```

Commits follow Conventional Commits.
Releases are versioned and tagged automatically from `main`.
