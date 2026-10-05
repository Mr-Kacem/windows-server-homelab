# Windows Server Home Lab

I started this lab after passing LFCS. I want to add Windows Server to what I already practice with Linux and understand how both environments are administered.

I document each step while I do it: what I change, why, and how I check the result.

## Environment

Windows Server 2025 Standard Evaluation runs in a Proxmox VM named `dc01` (VM ID `105`). `DC01` is now the first domain controller for `lab.home.arpa`.

I added a Windows 11 Enterprise Evaluation client in VM `win11-client01` (`106`). Its initial setup is in progress.

The host, storage, and Linux services are documented in my [proxmox-homelab](https://github.com/Mr-Kacem/proxmox-homelab) repository.

## Progress

Progress as of **5 October 2026**:

- [x] Install Windows Server and VirtIO drivers on Proxmox.
- [x] Configure `DC01`, static IPv4, and Windows updates.
- [x] Verify the baseline and create the `windows-base-ready` snapshot.
- [x] Create the `lab.home.arpa` forest with Active Directory Domain Services and DNS.
- [x] Verify domain services, DNS zones, and the LDAP SRV record.
- [x] Create the `ad-ds-dns-ready` snapshot.
- [x] Create organizational units, four test users, and department security groups.
- [x] Verify users, groups, and group memberships with PowerShell.
- [ ] Create the planned `ad-structure-ready` snapshot.
- [x] Create Windows 11 client VM `106`, load VirtIO drivers, and reach initial setup (OOBE).
- [ ] Complete client setup with a local account, the `WIN11-CLIENT01` hostname, and domain DNS.
- [ ] Join the client to `lab.home.arpa` and verify a domain user login.
- [ ] Practice Group Policy.

**Open item:** On `DC01`, QEMU Guest Agent installation remains unresolved; its option is disabled in Proxmox.

## Documentation

- [VM creation and Windows Server installation](docs/01-vm-and-installation.md)
- [Initial Windows Server configuration](docs/02-initial-configuration.md)
- [Active Directory and DNS](docs/03-active-directory-and-dns.md)
- [Organizational units, users, and groups](docs/04-organizational-units-users-and-groups.md)
- [Windows 11 client installation](docs/05-windows-11-client-installation.md)

I add new documents as the lab grows. Each one records the goal, configuration choices, checks, and any troubleshooting. Scripts and configuration examples will be added when I use them.

**Hamza Kacem**
