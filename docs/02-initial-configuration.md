# Initial Windows Server Configuration

**Date:** 1 October 2026

## Goal

Get `DC01` to a stable Windows baseline before installing Active Directory Domain Services and DNS.

## Configuration

| Setting | Value |
| --- | --- |
| Proxmox VM | `105` (`dc01`) |
| Operating system | Windows Server 2025 Standard Evaluation |
| Windows computer name | `DC01` |
| IPv4 address | `192.168.178.53` (static) |
| Default gateway | `192.168.178.1` |
| DNS server | `192.168.178.1` (FRITZ!Box) |

I kept the address already assigned to this server on the FRITZ!Box. At this stage, the router provides Internet access and DNS resolution.

## Work Completed

- Completed the first login and installed the VirtIO drivers.
- Renamed the Windows computer to `DC01`.
- Configured the static IPv4 settings above.
- Applied Windows updates and rebooted the server.

## Verification

The checks confirmed connectivity to the FRITZ!Box, public DNS name resolution, and the network configuration remaining correct after a reboot.

## QEMU Guest Agent

The QEMU Guest Agent did not install correctly. I disabled its option in Proxmox and left the installation issue open for a later attempt. The VirtIO drivers are installed.

## Baseline Snapshot

After completing the checks, I created the Proxmox snapshot **`windows-base-ready`**. It records the verified Windows baseline before adding server roles.

The next step is to install Active Directory Domain Services and DNS and promote `DC01` to the first domain controller in this lab.
