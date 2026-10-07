# Windows 11 Domain Join and Verification

**Date:** 7 October 2026  
**Client:** `WIN11-CLIENT01` / Proxmox VM `106`

## Goal

Join the Windows client to my domain and verify user access and OU placement before practicing Group Policy.

## Configuration and Login

| Setting | Value |
| --- | --- |
| Computer name | `WIN11-CLIENT01` |
| DNS server | `192.168.178.53` (`DC01`) |
| Domain | `lab.home.arpa` |
| Computer OU | `Company/Computers/Workstations` |

I configured DNS, renamed the client, and joined the domain. After restarting, Windows showed **Sign in to: LAB**. I successfully signed in as `LAB\marco.rossi`.

I also clarified the account types: `.\labadmin` is local, `LAB\Administrator` is the domain administrator, and `LAB\marco.rossi` is a domain user.

## OU Placement and Troubleshooting

On `DC01`, I found the new computer in the default `CN=Computers` container. An initial `Move-ADObject` attempt failed, so I checked the actual OU structure.

I moved the computer using Active Directory Users and Computers and corrected the OU name from `Workingstations` to `Workstations`. PowerShell confirmed the final distinguished name:

```text
CN=WIN11-CLIENT01,OU=Workstations,OU=Computers,OU=Company,DC=lab,DC=home,DC=arpa
```

To repeat the placement check on **DC01**:

```powershell
Get-ADComputer -Identity "WIN11-CLIENT01" |
    Select-Object Name, DistinguishedName
```

## Open Items and Next Step

- Planned client snapshot: **`domain-joined-ready`**. Creation is not yet confirmed.
- Windows displayed **`Windows license is expired`**. Activation/evaluation status still needs checking before treating the client as a final baseline.

Next, I will apply a first GPO to `Workstations` and verify the result on `WIN11-CLIENT01`.
