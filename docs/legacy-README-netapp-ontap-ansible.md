# netapp-ontap-ansible

Ansible playbooks for NetApp ONTAP storage automation, including a structured learning path (00-08).

## Contents

| Path | Purpose |
|------|---------|
| `ONTAP-Learning/` | 9-section Ansible for ONTAP learning series |
| `ONTAP-Learning/00-Lab Setup/` | Lab prerequisites |
| `ONTAP-Learning/01-Install Ansible/` | Ansible installation on CentOS |
| `ONTAP-Learning/02-Update NetApp Modules/` | Module update procedures |
| `ONTAP-Learning/03-understanding playbooks/` | Playbook structure basics |
| `ONTAP-Learning/04-First Playbook Example/` | Volume create/delete |
| `ONTAP-Learning/05-Complete Workflow/` | Full SVM + volume workflow |
| `ONTAP-Learning/06-Just the Facts/` | Gathering ONTAP facts |
| `ONTAP-Learning/07-Ansible Vault/` | Credential management |
| `ONTAP-Learning/08-Ansible Roles for ONTAP/` | Role-based automation |

## Prerequisites

- Ansible 2.14+
- `netapp.ontap` collection: `ansible-galaxy collection install netapp.ontap`
- ONTAP cluster with management LIF accessible

## Quick Start

```bash
ansible-playbook "ONTAP-Learning/04-First Playbook Example/volume.yml" --ask-vault-pass
```

## CI/CD

All PRs validated by ansible-lint, secret scan, and header compliance.

## Owner

humbledgeeks-allen | [HumbledGeeks.com](https://humbledgeeks.com)
