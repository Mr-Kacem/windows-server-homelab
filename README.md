# Windows Server Home Lab

I started this lab after passing LFCS. I want to add Windows Server to what I already practice with Linux and understand how both environments are administered.

I document each step while I do it: what I change, why, and how I check the result.

## Environment

Windows Server 2025 Standard Evaluation runs in a Proxmox VM named `dc01` (VM ID `105`). The host, storage, and Linux services are documented in my [proxmox-homelab](https://github.com/Mr-Kacem/proxmox-homelab) repository.

## Progress

Verified on **1 October 2026**:

- [x] Create the VM and install Windows Server.
- [x] Complete the first login and install the VirtIO drivers.
- [x] Rename the Windows computer to `DC01` and configure static IPv4.
- [x] Apply Windows updates and verify networking after a reboot.
- [x] Create the `windows-base-ready` Proxmox snapshot.
- [ ] Install Active Directory Domain Services and DNS, then promote `DC01` to a domain controller.

**Open item:** QEMU Guest Agent installation remains unresolved; its option is disabled in Proxmox.

## Documentation

- [VM creation and Windows Server installation](docs/01-vm-and-installation.md)
- [Initial Windows Server configuration](docs/02-initial-configuration.md)

I add new documents as the lab grows. Each one records the goal, configuration choices, checks, and any troubleshooting. Scripts and configuration examples will be added when I use them.

**Hamza Kacem**
