# Automation (personal Ansible collection)

This repository is my **personal Ansible automation collection** for day-to-day tasks.
It’s **not intended for publication on Ansible Galaxy**.

The directory layout follows the Ansible collection structure:
<https://docs.ansible.com/projects/ansible/latest/dev_guide/developing_collections_structure.html>

## Quick start

This repo is set up to be run via **`ansible-navigator`** using a pinned **execution environment** image (`ansible-navigator.yaml`).

- **Inventory**: `hosts.yaml` (see `ansible.cfg`)
- **Defaults/config**: `ansible.cfg`
- **Execution environment**: container image configured in `ansible-navigator.yaml`

Example (replace with your playbook name):

```bash
ansible-navigator run playbooks/<playbook>.yml
```

## Execution environment (container image)

Published image tags:
<https://quay.io/repository/rbohne/automation?tab=tags>

The execution environment build definition lives in:
- [meta/execution-environment.yml](meta/execution-environment.yml)

Build instructions are documented here:
- [meta/README.md](meta/README.md)

### Updating the pinned image

[ansible-navigator.yaml](ansible-navigator.yaml) pins a specific tag, for example:

```yaml
ansible-navigator:
  execution-environment:
    image: quay.io/rbohne/automation:ee-YYYYMMDDHHMM
```

After publishing a new image tag, update [ansible-navigator.yaml](ansible-navigator.yaml) to point at it.
