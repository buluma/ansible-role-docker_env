# Ansible role [docker_env](https://galaxy.ansible.com/ui/standalone/roles/buluma/docker_env/documentation)

Prepare Docker Environment for local testing.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-docker_env/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-docker_env/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-docker_env.svg)](https://github.com/buluma/ansible-role-docker_env/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-docker_env.svg)](https://github.com/buluma/ansible-role-docker_env/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-docker_env.svg)](https://github.com/buluma/ansible-role-docker_env/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/docker_env)](https://galaxy.ansible.com/ui/standalone/roles/buluma/docker_env/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-docker_env/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: localhost
  serial:
    - 1
    - 2
    - 25%
    - 50%
  vars:
    prepare_ubuntu: true
    prepare_centos: true
    prepare_rockylinux: true
    prepare_fedora: true
    prune_ubuntu: false
    prune_centos: false
    prune_rockylinux: false
    prune_fedora: false
    container_default_behavior: 'compatibility'

  roles:
    - role: buluma.docker_env
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-docker_env/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-docker_env/blob/master/defaults/main.yml):

```yaml
---
# defaults file for docker_env

# default container variables
state: started
command: sleep 1d
privileged: yes
interactive: yes
tty: yes
volumes:
  - /sys/fs/cgroup:/sys/fs/cgroup:rw
capabilities:
  - SYS_ADMIN
restart_policy: unless-stopped
container_default_behavior: no_defaults

# pull images/create containers
prepare_ubuntu: false
prepare_centos: false
prepare_rockylinux: false
prepare_fedora: false

# delete containers
prune_rockylinux: false
prune_centos: false
prune_ubuntu: false
prune_fedora: false

# prune everything, i.e. docker system prune
prune_everything: false
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-docker_env/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.epel](https://galaxy.ansible.com/buluma/epel)|[![Ansible Molecule](https://github.com/buluma/ansible-role-epel/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-epel/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-epel.svg)](https://github.com/shadowwalker/ansible-role-epel)|
|[buluma.python_pip](https://galaxy.ansible.com/buluma/python_pip)|[![Ansible Molecule](https://github.com/buluma/ansible-role-python_pip/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-python_pip/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-python_pip.svg)](https://github.com/shadowwalker/ansible-role-python_pip)|
|[buluma.docker](https://galaxy.ansible.com/buluma/docker)|[![Ansible Molecule](https://github.com/buluma/ansible-role-docker/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-docker/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-docker.svg)](https://github.com/shadowwalker/ansible-role-docker)|

## [Dependencies](#dependencies)

Most roles require some kind of preparation, this is done in `molecule/default/prepare.yml`. This role has a "hard" dependency on the following roles:

- {'role': 'buluma.docker', 'when': "environment == 'production'"}

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-docker_env/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Alpine](https://hub.docker.com/repository/docker/buluma/alpine/general)|all|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|
|[Fedora](https://hub.docker.com/repository/docker/buluma/fedora/general)|38, 39|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|
|[opensuse](https://hub.docker.com/repository/docker/buluma/opensuse/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-docker_env/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-docker_env/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-docker_env/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)


Template inspired by [Robert de Bock](https://github.com/robertdebock)
