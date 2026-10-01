# Windows Server Home Lab

I started this lab after passing LFCS. I want to add Windows Server to what I already practice with Linux and understand how both environments are administered.

I document each step while I do it: what I change, why, and how I check the result.

## Environment

Windows Server runs in a Proxmox VM named `dc01` (VM ID `105`). The host, storage, and Linux services are documented in my [proxmox-homelab](https://github.com/Mr-Kacem/proxmox-homelab) repository.

## Progress

Verified on **30 September 2026**:

- [x] Create the VM and attach the Windows Server and VirtIO installation media.
- [x] Install Windows Server and boot to the Windows lock screen.
- [ ] Complete the first login and check the VirtIO drivers.
- [ ] Configure the Windows hostname, networking, and updates.

## Documentation

- [VM creation and Windows Server installation](docs/01-vm-and-installation.md)

I add new documents as the lab grows. Each one records the goal, configuration choices, checks, and any troubleshooting. Scripts and configuration examples will be added when I use them.

**Hamza Kacem**
