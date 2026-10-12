# Windows Server Home Lab

I started this lab after passing LFCS. I want to add Windows Server to what I already practice with Linux and understand how both environments are administered.

I document each step while I do it: what I change, why, and how I check the result.

I study each topic through basic theory, a guided exercise, independent practice, and a recap.

## Environment

Windows Server 2025 Standard Evaluation runs in a Proxmox VM named `dc01` (VM ID `105`). `DC01` is now the first domain controller for `lab.home.arpa`.

Windows 11 Enterprise Evaluation runs in VM `win11-client01` (`106`) as `WIN11-CLIENT01`, joined to the domain.

The host, storage, and Linux services are documented in my [proxmox-home-lab](https://github.com/Mr-Kacem/proxmox-home-lab) repository.

## Progress

Progress as of **12 October 2026**:

- [x] Install Windows Server with VirtIO drivers, static IPv4, and Windows updates.
- [x] Verify the baseline and create the `windows-base-ready` snapshot.
- [x] Create `lab.home.arpa` with AD DS and DNS; verify services, DNS zones, and the LDAP SRV record.
- [x] Create the `ad-ds-dns-ready` snapshot.
- [x] Create OUs, four test users, and department security groups; verify memberships.
- [ ] Create the planned `ad-structure-ready` snapshot.
- [x] Install and configure Windows 11 client VM `106` with VirtIO drivers, a local account, and domain DNS.
- [x] Join the client to `lab.home.arpa` and verify a domain user login.
- [x] Place the computer in `Company/Computers/Workstations` and verify its distinguished name.
- [ ] Create the planned client snapshot `domain-joined-ready`.
- [x] Create a user GPO linked to `Company/Users/IT` and verify Control Panel/Settings restrictions on the client.
- [ ] Create the planned `DC01` snapshot `gpo-it-block-control-panel`.
- [x] Consolidate GPO scope, inheritance, precedence, account types, and the role of domain DNS.
- [x] Create a computer GPO and verify its logon notice on `WIN11-CLIENT01`.
- [x] Independently create a Sales user GPO and verify it with `LAB\luca.romano`.
- [x] Configure Sales share permissions for `GG_Sales`; verify Luca can create files and Laura is denied access.
- [ ] Practice NTFS inheritance and effective permissions.

**Open items:**

- On `DC01`, QEMU Guest Agent installation remains unresolved; its option is disabled in Proxmox.
- Investigate the Windows 11 warning `Windows license is expired`.

## Documentation

- [VM creation and Windows Server installation](docs/01-vm-and-installation.md)
- [Initial Windows Server configuration](docs/02-initial-configuration.md)
- [Active Directory and DNS](docs/03-active-directory-and-dns.md)
- [Organizational units, users, and groups](docs/04-organizational-units-users-and-groups.md)
- [Windows 11 client installation](docs/05-windows-11-client-installation.md)
- [Windows 11 domain join and verification](docs/06-windows-11-domain-join.md)
- [First Group Policy: Control Panel restriction](docs/07-first-group-policy.md)
- [Group Policy consolidation and practice](docs/08-group-policy-consolidation.md)
- [Security groups and share permissions](docs/09-security-groups-and-share-permissions.md)

Each document records what I changed, how I checked it, and any issues. I add scripts and configuration examples when I use them.

**Hamza Kacem**
