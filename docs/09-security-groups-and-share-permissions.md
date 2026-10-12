# Security Groups and File Share Permissions

**Date:** 12 October 2026  
**Share:** `\\DC01\Sales`

## Goal

Control access to a departmental share through a security group and verify both allowed and denied access.

## Configuration

I assigned access to `GG_Sales` for the Sales share. For normal user access, I used:

| Permission layer | Group permissions |
| --- | --- |
| Share | Change + Read |
| NTFS | Modify |

Share permissions control network access. NTFS permissions control operations on files and folders. I assigned permissions to the group, so access is managed through membership.

I also reviewed departmental separation using folders such as `C:\Shares\HR` and `C:\Shares\Sales`.

## Verification

| Test user | Membership in `GG_Sales` | Observed result |
| --- | --- | --- |
| Luca Romano | Member | Access to `\\DC01\Sales` allowed; file creation succeeded. |
| Laura Verdi | Non-member | Access to `\\DC01\Sales` denied. |

Both the positive and negative access checks passed. I completed the theory, guided exercise, independent practice, and recap for this topic.

## Next Step

Study NTFS inheritance and effective permissions, including how Windows determines access when a user belongs to multiple groups.
