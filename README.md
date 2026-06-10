# Windows Server File Server Permissions Lab

### Overview
- This lab demonstrates a Windows Server file server environment using Active Directory, DNS, domain users, security groups, SMB shared folders, share permissions, NTFS permissions, and domain-joined client testing.
- The goal of this lab was to simulate a small business file server where department users can access only their assigned shared folders.

------------------------------------------------------------
### Lab Environment
- Server Name: DC1
- Server OS: Windows Server 2022
- Client Name: PC1
- Client OS: Windows 11
- Domain: amir.local
- Network: VirtualBox Internal Network - AD-Lab  

------------------------------------------------------------
### IP Addressing
- DC1: 192.168.10.10
- PC1: 192.168.10.50
- DNS Server: 192.168.10.10  

------------------------------------------------------------
### Active Directory Structure
Organizational Units:
- IT
- HR
- Sales
- Groups
- Workstations  

------------------------------------------------------------
### Users
- ali.it
- sara.admin
- john.hr
- mike.sales  

------------------------------------------------------------
### Security Groups
- IT-Group
- HR-Group
- Sales-Group  

------------------------------------------------------------
### Group Membership
- IT-Group: ali.it, sara.admin
- HR-Group: john.hr
- Sales-Group: mike.sales  

------------------------------------------------------------
### Shared Folders
- \\DC1\IT
- \\DC1\HR
- \\DC1\Sales  

------------------------------------------------------------
### Permission Design
- IT-Group can access the IT shared folder.
- HR-Group can access the HR shared folder.
- Sales-Group can access the Sales shared folder.  

Users from other departments are denied access.

------------------------------------------------------------
### Share Permissions
- IT Share: IT-Group = Change, Domain Admins = Full Control
- HR Share: HR-Group = Change, Domain Admins = Full Control
- Sales Share: Sales-Group = Change, Domain Admins = Full Control  

------------------------------------------------------------
### NTFS Permissions
- IT Folder: IT-Group = Modify
- HR Folder: HR-Group = Modify
- Sales Folder: Sales-Group = Modify  

SYSTEM, Administrators, and Domain Admins have Full Control.

------------------------------------------------------------
### Skills Demonstrated
- Windows Server administration
- Active Directory Domain Services
- DNS configuration
- Domain user management
- Security group management
- Windows client domain join
- SMB file sharing
- Share permissions
- NTFS permissions
- Group-based access control
- Access denied troubleshooting
- Command Prompt verification  

------------------------------------------------------------
### Verification
- The Windows 11 client successfully joined the amir.local domain.
- Domain users were able to log in from PC1.
- Each department user successfully accessed their assigned shared folder.
- Unauthorized access attempts were denied.
- DNS resolution, domain login, group membership, and shared folder access were verified using Command Prompt.

------------------------------------------------------------
### Troubleshooting Notes
### Issue:
- PC1 cannot join the domain.

Cause:
- PC1 DNS was not pointing to the domain controller.

Fix:
- Set PC1 preferred DNS server to 192.168.10.10 and verify nslookup amir.local.

------------------------------------------------------------
### Issue:
- User cannot access the correct shared folder.

Cause:
- The user is not a member of the correct Active Directory security group or permissions are missing.

Fix:
- Verify group membership, share permissions, and NTFS permissions. Log out and log back in after changing group membership.

------------------------------------------------------------
### Issue:
-  Wrong user can access a department folder.

Cause:
- Broad permissions such as Everyone, Domain Users, or Authenticated Users may still exist.

Fix:
- Remove broad permissions and allow only the correct department security group.

------------------------------------------------------------
### Issue:
- User can open the folder but cannot create files.

Cause:
- User has Read permission instead of Modify or Change permission.

Fix:
- Set share permission to Change and NTFS permission to Modify.

------------------------------------------------------------
### Final Result
- A Windows Server file server was successfully configured with department-based access control. Active Directory security groups were used to manage permissions. IT, HR, and Sales users could access only their assigned folders, while unauthorized access attempts were denied.
- This lab demonstrates practical Windows Server, Active Directory, DNS, file sharing, permissions, and troubleshooting skills.
