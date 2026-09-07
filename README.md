# netapp-ontap

Reusable **NetApp** automation for **ONTAP** and **StorageGRID**.

## Contents

| Path | Language | What it does | Effect |
|---|---|---|---|
| `powershell/Install_NetAPP_NFS_Plugin.ps1` | PowerShell (VMware PowerCLI, esxcli) | Installs the NetApp NFS VAAI plug-in VIB on ESXi hosts | **changes hosts** (VIB install; supports review before execution) |
| `powershell/storagegrid/get-sg-grid-health.ps1` | PowerShell (`Invoke-RestMethod`) | StorageGRID grid health, node status, tenant summary | read-only |
| `ansible/storagegrid/sg-gather-grid-info.yml` | Ansible (`uri`, StorageGRID REST) | Grid health and node information | read-only |
| `docs/README-AsBuilt.md` | — | How to produce an ONTAP as-built report with AsBuiltReport.NetApp.ONTAP | — |
| `docs/ONTAP-Cluster-Deployment-Playbook.txt` | — | Phase/section reference of ONTAP cluster deployment commands with `<PLACEHOLDER>` values | — |
| `docs/legacy-README-*.md` | — | Original per-repository READMEs | — |

## Prerequisites

- PowerShell 7 recommended. `DataONTAP` / `NetApp.ONTAP` module for ONTAP work; VMware PowerCLI for the NFS plug-in installer.
- StorageGRID: an admin node reachable over HTTPS; no extra modules.
- Ansible: run with `--ask-vault-pass`.

## Environment-specific configuration

The deployment command reference in `docs/` uses `<PLACEHOLDER>` values only; workbook-driven deployment tooling
and any environment records are kept outside this repository. Setup notes, serial lists and
training material from the previous repositories were deliberately not carried forward.

## Credentials and safety

No credentials are stored in this repository. PowerShell scripts prompt (`Get-Credential`) or read
environment variables; Ansible playbooks expect an Ansible Vault (`--ask-vault-pass`) providing the
`vault_*` variables named in `group_vars`. Never commit vault files, Clixml exports or `.env` files
(see `.gitignore`). Run output (reports, CSV, logs) is generated content and is git-ignored; keep it
outside the repository.

## Provenance

Consolidated from previous local automation repositories during the 2026 LabOps repository
cleanup. This repository starts with a fresh history; earlier history is retained locally only.
