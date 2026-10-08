# First Group Policy: Control Panel Restriction

**Date:** 8 October 2026  
**Domain:** `lab.home.arpa`

## Goal

Create my first GPO and check that a restriction configured on the domain controller reaches a domain user on the Windows client.

## Configuration

I used the Group Policy Management interface on `DC01` to create the GPO and link it directly to the IT user OU.

| Item | Value |
| --- | --- |
| GPO name | `GPO-IT-Block-Control-Panel` |
| Linked OU | `Company/Users/IT` |
| Policy path | User Configuration → Policies → Administrative Templates → Control Panel |
| Setting | Prohibit access to Control Panel and PC settings |
| State | Enabled |

This is a user policy. Marco Rossi's account belongs to the IT OU.

## Verification

I signed in to `WIN11-CLIENT01` as `LAB\marco.rossi` and tested access to Control Panel and Settings. Both were blocked.

The test confirmed that the GPO linked to the user's OU was applied successfully on the client.

## Recovery Point and Next Step

Planned `DC01` snapshot: **`gpo-it-block-control-panel`**. Its creation still needs confirmation.

Next, I will add further GPOs and verify their effect on the client.
