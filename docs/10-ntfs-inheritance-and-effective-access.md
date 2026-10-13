# NTFS Inheritance and Effective Access

**Date:** 13 October 2026  
**Folder:** `C:\Shares\HR\Payroll`

## Goal

Give payroll staff access to a protected subfolder while keeping the parent HR folder available to the wider HR group.

## Configuration

I created `Payroll` and confirmed that it inherited permissions from `HR`, using the **Inherited from** column.

I used **Disable inheritance** and converted the inherited entries to explicit permissions. I then:

- Created `GG_HR_Payroll`, added Laura Verdi, and granted the group NTFS **Modify** on `Payroll`.
- Removed the `GG_HR` and `Users` entries from `Payroll`.
- Retained the entries for `Administrators`, `SYSTEM`, and `CREATOR OWNER`.

The departmental group grants are:

| Folder | Group | NTFS permission |
| --- | --- | --- |
| `C:\Shares\HR` | `GG_HR` | Modify |
| `C:\Shares\HR\Payroll` | `GG_HR_Payroll` | Modify |

As my independent exercise, I created Sofia Conti and added her to `GG_HR`. She is not a member of `GG_HR_Payroll`.

## Verification

I checked Laura's and Sofia's NTFS permissions through the **Effective Access** GUI, then tested access on `WIN11-CLIENT01`.

| Test user | Relevant groups | Observed result |
| --- | --- | --- |
| Laura Verdi | `GG_HR`, `GG_HR_Payroll` | Payroll access allowed; created `Test-Laura.txt`. |
| Sofia Conti | `GG_HR` | HR access allowed; Payroll access denied. |

Both positive and negative access tests passed.

## Next Step

Use Group Policy Preferences to map network shares automatically for domain users.
