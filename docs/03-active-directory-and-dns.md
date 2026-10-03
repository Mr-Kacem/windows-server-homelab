# Active Directory and DNS

**Date:** 3 October 2026  
**VM:** `105` / `DC01`

## Goal

Turn `DC01` into the first domain controller in my lab, ready for exercises with organizational units, users, groups, and Group Policy.

## Configuration

| Setting | Value |
| --- | --- |
| Forest / domain | `lab.home.arpa` |
| NetBIOS name | `LAB` |
| Domain controller | `dc01.lab.home.arpa` |
| IPv4 address | `192.168.178.53` |
| Network adapter DNS | `192.168.178.53` |
| Administrator login | `LAB\Administrator` |

## Work Completed

I installed Active Directory Domain Services through Server Manager and promoted `DC01` to a domain controller, creating a new forest. DNS Server was installed during the promotion.

After the reboot, I signed in as `LAB\Administrator`. I changed the network adapter DNS from the FRITZ!Box to `192.168.178.53`, so `DC01` now uses its own DNS server.

## Verification

```powershell
Get-ADDomain
Get-DnsServerZone
Resolve-DnsName -Type SRV _ldap._tcp.dc._msdcs.lab.home.arpa
```

The checks confirmed:

- `DNSRoot` and `NetBIOSName` match the configuration above.
- `NTDS`, `DNS`, and `Netlogon` services are running.
- `lab.home.arpa` and `_msdcs.lab.home.arpa` are AD-integrated zones with secure dynamic updates.
- The LDAP SRV record points to `dc01.lab.home.arpa`, resolving to `192.168.178.53`.
- Internal and external DNS resolution works.

`dcdiag /test:dns` reported a warning; subsequent DNS zone and lookup checks succeeded.

## Recovery Point

I created the Proxmox snapshot **`ad-ds-dns-ready`** before starting the organizational structure and Group Policy exercises.

QEMU Guest Agent remains uninstalled, with its option disabled in Proxmox.
