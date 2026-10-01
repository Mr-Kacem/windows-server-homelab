# VM Creation and Windows Server Installation

**Date:** 30 September 2026  
**VM:** `dc01` / `105`

## Goal

Add a Windows Server VM to my existing Proxmox lab and get it ready for administration exercises.

## VM Configuration

| Setting | Value |
| --- | --- |
| VM name / ID | `dc01` / `105` |
| CPU | 2 vCPU, CPU type `host` |
| Memory | 4 GiB, ballooning disabled |
| Disk | 64 GiB on `local-lvm` |
| Disk controller | VirtIO SCSI single |
| Network | VirtIO, bridge `vmbr0` |
| Machine / firmware | Q35 / OVMF (UEFI) |
| TPM | Version 2.0 |
| Installation media | Windows Server Evaluation ISO and Fedora VirtIO driver ISO |

I started with 2 vCPU and 4 GiB RAM to keep the VM small on my 16 GiB host. I attached the VirtIO ISO so the drivers are available during setup and initial configuration.

## Work Completed

1. Transferred both ISOs to Proxmox.
2. Created the VM with the settings above and kept TPM enabled.
3. Attached the Windows Server and VirtIO ISOs.
4. Started Windows setup and selected the US keyboard layout.
5. Installed Windows Server and reached the Windows lock screen.

## Verification

The Proxmox summary shows VM `105` running with 2 CPUs and a 64 GiB boot disk. The console displays **“Press Ctrl+Alt+Delete to unlock.”** This confirms that the installed system boots.

## Open Items

Ubuntu intercepted `Ctrl+Alt+Delete` from my physical keyboard, so completing the first login through the Proxmox console is the next step.

The Windows version and edition, installed drivers, guest agent, hostname, and network settings will be recorded after checking them in Windows.
