# Windows 11 Client Installation

**Date:** 5 October 2026  
**Proxmox VM:** `win11-client01` / `106`

## Goal

Add a Windows 11 client to test domain joins, domain user logins, and later Group Policy.

## VM Configuration

| Setting | Value |
| --- | --- |
| Operating system | Windows 11 Enterprise Evaluation, x64 |
| CPU / memory | 2 vCPU / 4 GB RAM |
| Disk / controller | 64 GB / VirtIO SCSI |
| Machine / firmware | Q35 / OVMF (UEFI) |
| TPM | Version 2.0 |
| Network | VirtIO on `vmbr0` |
| Driver ISO | `virtio-win-0.1.302.iso` |

## Work Completed

I downloaded the official Windows ISO from Microsoft Evaluation Center, transferred it to Proxmox with `scp`, and placed it in the local ISO storage.

I created the VM and attached the VirtIO ISO. During Windows setup, I manually loaded the VirtIO SCSI driver so the installer could detect the disk. I then loaded the network driver from `NetKVM/w11/amd64`, which made the VirtIO adapter available.

## Status on 5 October 2026

Installation reached the first-run setup (OOBE), at **“Let's set things up for your work or school.”**

I planned to use **Sign-in options → Domain join instead** to create a local account and finish setup. Joining Active Directory remains a separate step afterward.

## Next Steps Identified on 5 October 2026

1. Finish OOBE with a local account and reach the desktop.
2. Rename the computer to `WIN11-CLIENT01`, set DNS to `192.168.178.53`, and verify resolution of `lab.home.arpa`.
3. Join `lab.home.arpa` and restart the client.
4. Sign in with a domain user.
5. Move the computer account to `Company/Computers/Workstations` and verify it from `DC01`.
6. Create a final Proxmox snapshot.

## Follow-up — 7 October 2026

Client setup, DNS configuration, domain join, domain user login, and OU placement are now complete; see [Windows 11 domain join and verification](06-windows-11-domain-join.md).

The client snapshot `domain-joined-ready` is planned; its creation still needs confirmation.
