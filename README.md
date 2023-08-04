# ansible-role-glab

[![molecule](https://github.com/diodonfrost/ansible-role-glab/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-glab/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.glab-660198.svg)](https://galaxy.ansible.com/diodonfrost/glab)

This role provide a compliance for install glab on your target host.

## Requirements

None.

## Role Variables

This role has multiple variables. The defaults for all these variables are the following:

```yaml
---
# defaults file for ansible-role-glab

# Define glab version to install
# Default: latest
glab_version: latest

# Define where to download glab package url
# Default: use local system path defined in Ansible vars/*.yml
glab_pkg_url: "{{ default_glab_pkg_url }}"

# Define where to install glab binary
# Default: use local system path defined in Ansible vars/*.yml
glab_bin_directory: "{{ default_glab_bin_directory }}"
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy glab role in a localhost and installing the latest version of glab.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.glab
```

This role can also install a specific version of glab.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.glab
      vars:
        glab_version: v1.31.0
```

## Local Testing

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](https://www.virtualbox.org/) (if you test windows system)
* [Vagrant](https://www.vagrantup.com/downloads.html) (if you test windows system)

### Testing with Docker

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 22.04
molecule test

# Test ansible role with ubuntu 20.04
image=ansible-ubuntu:20.04 molecule test

# Test ansible role with alpine latest
image=ansible-alpine:latest molecule test

# Create ubuntu 22.04 instance
molecule create

# Apply role on ubuntu 22.04 instance
molecule converge

# Launch tests on ubuntu 22.04 instance
molecule verify
```

### Testing with Vagrant and Libvirt

```shell
# Test ansible role with Windows
molecule test -s windows
```

## License

Apache 2

## Author Information

This role was created in 2023 by diodonfrost.
