# Doсkerfile: Ubuntu-18.04 for Molecule CI 

[![Build](https://github.com/darexsu/docker-ubuntu-1804/actions/workflows/build.yml/badge.svg)](https://github.com/darexsu/docker-ubuntu-1804/actions/workflows/build.yml)
[![Docker pulls](https://img.shields.io/docker/pulls/darexsu/molecule-ubuntu-1804.svg?maxAge=2592000)](https://hub.docker.com/r/darexsu/molecule-ubuntu-1804/)

Pre-build Ubuntu-18.04. Image already has Ansible inside, so Molecule doesn't need to waste time building it.

### Example molecule.yml
```yaml
---
dependency:
  name: galaxy
driver:
  name: docker
platforms:
  - name: instance
    image: "darexsu/molecule-ubuntu-1804:latest"
    command: ${MOLECULE_DOCKER_COMMAND:-""}
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
    privileged: true
    pre_build_image: true
provisioner:
  name: ansible
  playbooks:
    converge: converge.yml
```
