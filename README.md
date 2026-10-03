# Active Directory Troubleshooting Lab

A home lab where I built a Windows domain environment and documented the real problems I ran into while setting it up. Each log follows the same troubleshooting process I'd use on a help desk ticket: identify the issue, diagnose, form a theory, test it, fix it, and validate the fix.

## Lab Environment
- **Hypervisor:** Oracle VirtualBox v7.2.8
- **Server:** Windows Server 2019 (Domain Controller running AD DS, DHCP, and DNS)
- **Client:** Windows 10 Pro (domain-joined)
- **Structure:** Organizational Units (OUs) such as _USERS and _ADMINS, with Group Policy Objects (GPOs) linked to each

## Troubleshooting Logs

| # | Issue | Area | Key Tools |
|---|-------|------|-----------|
| 1 | [GPO Conflict](01-gpo-conflict.md) | Group Policy | `gpresult`, Group Policy Management |
| 2 | [Internet Connection Failed](02-internet-connection-failed.md) | Networking | `ipconfig`, `systeminfo`, network reset |
| 3 | [DHCP Authorization Disconnect](03-dhcp-authorization.md) | DHCP | DHCP Manager, `ipconfig` |
| 4 | [Cached NCSI Status](04-ncsi-cached-status.md) | Networking | `ipconfig`, `ping`, VirtualBox network settings |
| 5 | [Account Lockout Policy](05-account-lockout-policy.md) | Group Policy | `gpresult`, Default Domain Policy |
| 6 | [No Reverse Lookup Zone](06-reverse-lookup-zone.md) | DNS | `nslookup`, DNS Manager |

## Skills Demonstrated
- Diagnosing and fixing Group Policy linking and conflict issues
- Using `gpresult` to see which policies apply to a user or computer
- Troubleshooting IP configuration and APIPA addresses with `ipconfig`
- Configuring and re-authorizing DHCP on a domain controller
- Creating DNS reverse lookup zones and PTR records
- Testing hypotheses one at a time and validating every fix
- Writing clear documentation so another technician can follow what I did

## My Troubleshooting Process
Every log uses the same format:
1. **Issue:** what's wrong and what the user sees
2. **Diagnostics:** what I checked first
3. **Probable cause and testing theory:** what I suspected and how I tested it
4. **Plan of action:** the fix
5. **Validation:** how I confirmed it worked
6. **Documentation:** a short summary for the next person

## About Me
Aspiring help desk / IT support specialist building hands-on experience with Windows Server and Active Directory. Currently working toward CompTIA A+ and CCNA.

- LinkedIn: [www.linkedin.com/in/yosef-tomas-399556411]
