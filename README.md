# Windows Server Home Lab

I started this lab after passing LFCS. I want to add Windows Server to what I already practice with Linux and understand how both environments are administered.

I document each step while I do it: what I change, why, and how I check the result.

## Environment

Windows Server 2025 Standard Evaluation runs in a Proxmox VM named `dc01` (VM ID `105`). `DC01` is now the first domain controller for `lab.home.arpa`.

The host, storage, and Linux services are documented in my [proxmox-homelab](https://github.com/Mr-Kacem/proxmox-homelab) repository.

## Progress

Verified on **3 October 2026**:

- [x] Install Windows Server and VirtIO drivers on Proxmox.
- [x] Configure `DC01`, static IPv4, and Windows updates.
- [x] Verify the baseline and create the `windows-base-ready` snapshot.
- [x] Create the `lab.home.arpa` forest with Active Directory Domain Services and DNS.
- [x] Verify domain services, DNS zones, and the LDAP SRV record.
- [x] Create the `ad-ds-dns-ready` snapshot.
- [ ] Create organizational units, users, and groups.
- [ ] Practice Group Policy.

**Open item:** QEMU Guest Agent installation remains unresolved; its option is disabled in Proxmox.

## Documentation

- [VM creation and Windows Server installation](docs/01-vm-and-installation.md)
- [Initial Windows Server configuration](docs/02-initial-configuration.md)
- [Active Directory and DNS](docs/03-active-directory-and-dns.md)

I add new documents as the lab grows. Each one records the goal, configuration choices, checks, and any troubleshooting. Scripts and configuration examples will be added when I use them.

**Hamza Kacem**
