# [Ansible role docker_env](#docker_env)

Prepare Docker Environment for local testing.

|GitHub|GitLab|Downloads|Version|Issues|Pull Requests|
|------|------|-------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-docker_env/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-docker_env/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-docker_env/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-docker_env)|[![downloads](https://img.shields.io/ansible/role/d/4690)](https://galaxy.ansible.com/buluma/docker_env)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-docker_env.svg)](https://github.com/buluma/ansible-role-docker_env/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-docker_env.svg)](https://github.com/buluma/ansible-role-docker_env/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-docker_env.svg)](https://github.com/buluma/ansible-role-docker_env/pulls/)|

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
- name: prepare
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
  - /sys/fs/cgroup:/sys/fs/cgroup:ro
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

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.epel](https://galaxy.ansible.com/buluma/epel)|[![Build Status GitHub](https://github.com/buluma/ansible-role-epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-epel/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-epel/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-epel)|
|[buluma.python_pip](https://galaxy.ansible.com/buluma/python_pip)|[![Build Status GitHub](https://github.com/buluma/ansible-role-python_pip/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-python_pip/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-python_pip/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-python_pip)|
|[buluma.docker](https://galaxy.ansible.com/buluma/docker)|[![Build Status GitHub](https://github.com/buluma/ansible-role-docker/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-docker/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-docker/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-docker)|

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
|[Fedora](https://hub.docker.com/repository/docker/buluma/fedora/general)|34, 35|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|
|[opensuse](https://hub.docker.com/repository/docker/buluma/opensuse/general)|all|

The minimum version of Ansible required is 2.1, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-docker_env/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-docker_env/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-docker_env/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)

Please consider [sponsoring me](https://github.com/sponsors/buluma).

### [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
