Images for Ansible Molecule
===========================

Very basic images for use with [Ansible Molecule][molecule]. The intention is
to have ready-to-use images including a Python interpreter that works with the
most recent [target Python version that Ansible itself supports][ansible-core
support matrix] and systemd support to test Ansible roles with services.

**Note:** The images are not intended for production use, just for testing with
Molecule.


Table of Contents
-----------------

- [Images](#images)
- [Usage](#usage)
  * [non-systemd](#non-systemd)
  * [systemd](#systemd)


Images
------

You can find all images [here at the packages page][images]. Here is a concise
list with build status and image name:

- [![Arch Linux](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/archlinux.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/archlinux.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-archlinux:latest`
- [![Debian Bullseye](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/debian-bullseye.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/debian-bullseye.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-debian-bullseye:latest`
- [![Debian Bookworm](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/debian-bookworm.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/debian-bookworm.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-debian-bookworm:latest`
- [![Debian Trixie](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/debian-trixie.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/debian-trixie.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-debian-trixie:latest`
- [![Rocky Linux 8](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/rockylinux-8.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/rockylinux-8.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-rockylinux-8:latest`
- [![Rocky Linux 9](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/rockylinux-9.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/rockylinux-9.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-rockylinux-9:latest`
- [![Ubuntu Focal](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/ubuntu-focal.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/ubuntu-focal.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-ubuntu-focal:latest`
- [![Ubuntu Jammy](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/ubuntu-jammy.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/ubuntu-jammy.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-ubuntu-jammy:latest`
- [![Ubuntu Noble](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/ubuntu-noble.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/ubuntu-noble.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-ubuntu-noble:latest`


Usage
-----

### non-systemd

For simple non-systemd usage:

```yml
# .config/molecule/config.yml

driver:
  name: docker

platforms:

  - name: archlinux
    image: ghcr.io/idiv-biodiversity/ansible-molecule-archlinux:latest
    pre_build_image: yes
    groups:
      - nosudo

  - name: debian-bullseye
    image: ghcr.io/idiv-biodiversity/ansible-molecule-debian-bullseye:latest
    pre_build_image: yes
    groups:
      - nosudo

  - name: debian-bookworm
    image: ghcr.io/idiv-biodiversity/ansible-molecule-debian-bookworm:latest
    pre_build_image: yes
    groups:
      - nosudo

  - name: debian-trixie
    image: ghcr.io/idiv-biodiversity/ansible-molecule-debian-trixie:latest
    pre_build_image: yes
    groups:
      - nosudo

  - name: rockylinux-8
    image: ghcr.io/idiv-biodiversity/ansible-molecule-rockylinux-8:latest
    pre_build_image: yes
    groups:
      - nosudo

  - name: rockylinux-9
    image: ghcr.io/idiv-biodiversity/ansible-molecule-rockylinux-9:latest
    pre_build_image: yes
    groups:
      - nosudo

  - name: ubuntu-focal
    image: ghcr.io/idiv-biodiversity/ansible-molecule-ubuntu-focal:latest
    pre_build_image: yes
    groups:
      - nosudo

  - name: ubuntu-jammy
    image: ghcr.io/idiv-biodiversity/ansible-molecule-ubuntu-jammy:latest
    pre_build_image: yes
    groups:
      - nosudo

  - name: ubuntu-noble
    image: ghcr.io/idiv-biodiversity/ansible-molecule-ubuntu-noble:latest
    pre_build_image: yes
    groups:
      - nosudo

provisioner:
  name: ansible
  inventory:
    group_vars:
      nosudo:
        ansible_become_method: su
```

### systemd

To test roles with systemd services:

```yml
# .config/molecule/config.yml

driver:
  name: docker

platforms:

  - name: archlinux
    image: ghcr.io/idiv-biodiversity/ansible-molecule-archlinux:latest
    command: /usr/lib/systemd/systemd
    pre_build_image: yes
    privileged: yes
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    groups:
      - nosudo

  - name: debian-bullseye
    image: ghcr.io/idiv-biodiversity/ansible-molecule-debian-bullseye:latest
    command: /lib/systemd/systemd
    pre_build_image: yes
    privileged: yes
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    groups:
      - nosudo

  - name: debian-bookworm
    image: ghcr.io/idiv-biodiversity/ansible-molecule-debian-bookworm:latest
    command: /usr/lib/systemd/systemd
    pre_build_image: yes
    privileged: yes
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    groups:
      - nosudo

  - name: debian-trixie
    image: ghcr.io/idiv-biodiversity/ansible-molecule-debian-trixie:latest
    command: /usr/lib/systemd/systemd
    pre_build_image: yes
    privileged: yes
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    groups:
      - nosudo

  - name: rockylinux-8
    image: ghcr.io/idiv-biodiversity/ansible-molecule-rockylinux-8:latest
    command: /usr/lib/systemd/systemd
    pre_build_image: yes
    privileged: yes
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    groups:
      - nosudo

  - name: rockylinux-9
    image: ghcr.io/idiv-biodiversity/ansible-molecule-rockylinux-9:latest
    command: /usr/lib/systemd/systemd
    pre_build_image: yes
    privileged: yes
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    groups:
      - nosudo

  - name: ubuntu-focal
    image: ghcr.io/idiv-biodiversity/ansible-molecule-ubuntu-focal:latest
    command: /usr/lib/systemd/systemd
    pre_build_image: yes
    privileged: yes
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    groups:
      - nosudo

  - name: ubuntu-jammy
    image: ghcr.io/idiv-biodiversity/ansible-molecule-ubuntu-jammy:latest
    command: /usr/lib/systemd/systemd
    pre_build_image: yes
    privileged: yes
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    groups:
      - nosudo

  - name: ubuntu-noble
    image: ghcr.io/idiv-biodiversity/ansible-molecule-ubuntu-noble:latest
    command: /usr/lib/systemd/systemd
    pre_build_image: yes
    privileged: yes
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    groups:
      - nosudo

provisioner:
  name: ansible
  inventory:
    group_vars:
      nosudo:
        ansible_become_method: su
```


[ansible-core support matrix]: https://docs.ansible.com/ansible-core/devel/reference_appendices/release_and_maintenance.html#ansible-core-support-matrix
[molecule]: https://ansible.readthedocs.io/projects/molecule/
[images]: https://github.com/orgs/idiv-biodiversity/packages?repo_name=ansible-molecule-images
