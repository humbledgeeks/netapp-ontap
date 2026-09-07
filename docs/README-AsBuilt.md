# NetApp ONTAP — As-Built Report

Generates an As-Built document (Word + HTML) of an ONTAP cluster using
AsBuiltReport. Runs on macOS PowerShell 7 (NetApp.ONTAP 9.11+ is cross-platform).

## 1. Launch PowerShell

```bash
# macOS: install pwsh once if you don't have it
brew install --cask powershell
pwsh
```

Inside `pwsh`, trust the gallery once:

```powershell
Set-PSRepository -Name PSGallery -InstallationPolicy Trusted
```

## 2. Install / update the modules

```powershell
Install-Module AsBuiltReport.NetApp.ONTAP -Scope CurrentUser -AllowClobber -SkipPublisherCheck
# NetApp.ONTAP toolkit installs automatically as a dependency. To update later:
Update-Module AsBuiltReport.NetApp.ONTAP
Update-Module NetApp.ONTAP
```

## 3. One-time global config (company info, author)

```powershell
New-AsBuiltConfig      # note the JSON path it prints; reuse it with -AsBuiltConfigFilePath
```

## 4. Generate the As-Built

```powershell
$cred = Get-Credential
New-AsBuiltReport `
  -Report NetApp.ONTAP `
  -Target 10.0.0.10 `                                       # cluster management LIF
  -Credential $cred `
  -Format Html,Word `
  -OutputFolderPath "$HOME/AsBuiltReports" `
  -StyleFilePath "$HOME/AsBuiltReports/<Company>.Style.ps1" `    # optional company branding (see note)
  -EnableHealthCheck -Verbose
```

Replace `10.0.0.10` with your cluster management LIF / FQDN.

## Notes

- Works on macOS with a recent NetApp.ONTAP (9.11+). If import fails, update the
  toolkit: `Update-Module NetApp.ONTAP`.
- **Company logo / branding:** `-StyleFilePath` points to `<Company>.Style.ps1` (pending
  the logo template). Cover-image embedding uses `System.Drawing` (Windows-only),
  so the logo renders reliably only when generated on Windows. Remove the
  `-StyleFilePath` line until the style script exists.
