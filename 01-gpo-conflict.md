# Issue 1: Resolving Group Policy Object Conflict

**Environment:** Oracle VirtualBox v7.2.8 / Windows Server 2019 / Windows 10 Pro

## Issue
I could not access the Control Panel on either of my admin accounts on the Client and Server VMs.

## Diagnostics
On the Server, I ran `gpresult /r` to see which policies were affecting the user. All the GPOs I had linked to the _USERS OU were showing up.

## Probable Cause 1
The GPOs were not configured properly, or were not linked to the proper OUs.

## Testing Theory 1
- In Group Policy Management, I saw the GPOs were affecting every OU.
- I ran `gpresult /h gpreport.html` (from an admin Command Prompt) and opened it with `start gpreport.html`.
- The report confirmed the right OUs were getting the GPOs, but other OUs like _ADMINS were getting them too.

![GPO report](troubleshootingprior.png)

## Probable Cause 2
The GPOs were configured properly but were linked at the top of the domain.

## Testing Theory 2
In Group Policy Management, I confirmed the GPOs were linked directly under the domain.

![GPOs linked at domain level](screenshots/gpo-02-domain-links.png)

## Plan of Action
- Removed the links from the top of the domain (except the Default Domain Policy).
- Linked each GPO only to its corresponding OU.
- Ran `gpupdate /force`.

## Validation
- Admin account: Control Panel opens.
- Regular user on the client VM: Control Panel access denied.
- Re-ran `gpresult /h gpreport.html` to confirm.

![Validation](screenshots/gpo-03-validation.png)

*Note: the report still showed the Control Panel GPO because the report was cached. The GPO is no longer linked to _ADMINS.*

## Preventative Measures
Updated my GPO setup documentation to link GPOs at the lowest level possible.

## Documentation
All GPOs were linked at the top of the domain, so they applied to every OU beneath it. I removed those links and linked each GPO only to the OUs that needed it.
