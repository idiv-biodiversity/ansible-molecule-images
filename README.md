# Images for Ansible Molecule

Very basic images for use with [Ansible Molecule][molecule]. The intention is
to have ready-to-use images including a Python interpreter that works with the
most recent [target Python version that Ansible itself supports][ansible-core
support matrix] and systemd support to test Ansible roles with services.

**Note:** The images are not intended for production use, just for testing with
Molecule.

## Images

- [image overview](https://github.com/orgs/idiv-biodiversity/packages?repo_name=ansible-molecule-images)
- [![Arch Linux](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/archlinux.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/archlinux.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-archlinux:latest`
- [![Rocky Linux 8](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/rockylinux-8.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/rockylinux-8.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-rockylinux-8:latest`
- [![Rocky Linux 9](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/rockylinux-9.yml/badge.svg)](https://github.com/idiv-biodiversity/ansible-molecule-images/actions/workflows/rockylinux-9.yml) `ghcr.io/idiv-biodiversity/ansible-molecule-rockylinux-9:latest`


[ansible-core support matrix]: https://docs.ansible.com/ansible-core/devel/reference_appendices/release_and_maintenance.html#ansible-core-support-matrix
[molecule]: https://ansible.readthedocs.io/projects/molecule/
