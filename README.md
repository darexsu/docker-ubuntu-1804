# Doсkerfile: Ubuntu-18.04 for Molecule CI 

[![Build](https://github.com/darexsu/docker-ubuntu-1804/actions/workflows/build.yml/badge.svg)](https://github.com/darexsu/docker-ubuntu-1804/actions/workflows/build.yml)

Ubuntu-18.04 for Ansible Playbooks testing

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
provisioner:
  name: ansible
  playbooks:
    converge: converge.yml
```