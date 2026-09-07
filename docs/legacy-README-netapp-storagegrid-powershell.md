# netapp-storagegrid-powershell

PowerShell scripts for NetApp StorageGRID object storage automation via REST API.

## Contents

| File | Purpose |
|------|---------|
| `get-sg-grid-health.ps1` | Retrieve grid health status via StorageGRID management REST API |

## Prerequisites

- PowerShell 5.1+ or PowerShell 7+
- StorageGRID admin node accessible with valid credentials
- No additional modules required — uses native `Invoke-RestMethod`

## Quick Start

```powershell
.\get-sg-grid-health.ps1 -AdminNode <admin-node-ip>
```

## CI/CD

All PRs validated by PSScriptAnalyzer, secret scan, and header compliance.

## Owner

humbledgeeks-allen | [HumbledGeeks.com](https://humbledgeeks.com)
