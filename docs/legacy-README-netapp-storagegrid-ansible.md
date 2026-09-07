# netapp-storagegrid-ansible

Ansible playbooks for NetApp StorageGRID object storage automation.

## Contents

| File | Purpose |
|------|---------|
| `sg-gather-grid-info.yml` | Gather grid health and node information |

## Prerequisites

- Ansible 2.14+
- `netapp.storagegrid` collection: `ansible-galaxy collection install netapp.storagegrid`
- StorageGRID admin node accessible with a valid API auth token

## Quick Start

```bash
ansible-playbook sg-gather-grid-info.yml --ask-vault-pass
```

## CI/CD

All PRs validated by ansible-lint, secret scan, and header compliance.

## Owner

humbledgeeks-allen | [HumbledGeeks.com](https://humbledgeeks.com)
