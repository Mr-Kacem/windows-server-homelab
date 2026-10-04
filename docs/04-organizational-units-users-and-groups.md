# Organizational Units, Users, and Groups

**Date:** 4 October 2026  
**Domain:** `lab.home.arpa` / `DC01`

## Goal

Give the domain a small company structure before adding a Windows client and practicing Group Policy.

## OU Structure

I created the following organizational units through Active Directory Users and Computers. Paths below are relative to the domain.

| Parent | Child OUs |
| --- | --- |
| Domain root | `Company` |
| `Company` | `Users`, `Computers`, `Groups` |
| `Company/Users` | `IT`, `HR`, `Sales` |
| `Company/Computers` | `Workstations`, `Servers` |

## Users and Groups

I created three global security groups in `Company/Groups`: `GG_IT`, `GG_HR`, and `GG_Sales`. I placed four test users in their department OUs and added them to the matching groups.

| Test user | OU under `Company/Users` | Security group |
| --- | --- | --- |
| Marco Rossi | `IT` | `GG_IT` |
| Anna Bianchi | `IT` | `GG_IT` |
| Laura Verdi | `HR` | `GG_HR` |
| Luca Romano | `Sales` | `GG_Sales` |

## Verification

I checked the accounts with `Get-ADUser`, the groups with `Get-ADGroup`, and membership with `Get-ADGroupMember`. The results matched the structure and assignments above.

This helped me separate three concepts: OUs organize objects and provide a scope for Group Policy; users represent identities; security groups collect members for assigning access to resources.

## Recovery Point and Next Step

The planned Proxmox snapshot is **`ad-structure-ready`**. Its creation still needs confirmation.

Next, I will create `WIN11-CLIENT01`, join it to `lab.home.arpa`, and test a domain user login before working on Group Policy.
