# Group Policy: Consolidation and Practice

**Date:** 11 October 2026  
**Lab:** `DC01` / `WIN11-CLIENT01` / `lab.home.arpa`

## Goal

Consolidate the Active Directory and Group Policy basics, then put them into practice with a guided computer policy and an independent user policy.

## Concepts Reviewed

I reviewed:

- The different roles of OUs, security groups, and GPOs.
- User Configuration and Computer Configuration.
- GPO inheritance and precedence.
- Local and domain accounts, and the role of `DC01` DNS in Active Directory.

## Guided Exercise: Computer Policy

I created and tested **`GPO-Workstations-Logon-Notice`** as a computer GPO. The configured logon message appeared on `WIN11-CLIENT01`, confirming the test succeeded.

## Independent Exercise: Sales Policy

I created **`GPO-Sales-Block-Control-Panel-and-Settings`** and linked it to the `Sales` OU under `Company/Users`.

I signed in as `LAB\luca.romano` and verified the Control Panel/Settings restriction. This was my independent exercise after the guided practice.

## Result

I completed the full learning cycle: theory, guided exercise, independent practice, and verification. I checked both the computer logon notice and the user restriction in the lab.
