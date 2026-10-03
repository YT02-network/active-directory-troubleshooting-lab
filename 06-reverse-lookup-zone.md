# Issue 6: No Reverse Lookup Zone

**Environment:** Oracle VirtualBox v7.2.8 / Windows Server 2019 / Windows 10 Pro

## Issue
When I ran `nslookup yourdomain.local`, the domain name of the DC did not come back properly.

## Diagnostics
`nslookup yourdomain.local` returned the IP address of the DC, but the default server name showed as "Unknown." I ran `ipconfig /all` and found no issues with the IP configuration.

## Probable Cause
Since `nslookup` was not returning the DC's name, I suspected a DNS issue.

## Testing Theory
I checked the DNS Manager on the DC and found no problems with the DNS configuration. After reviewing all the tabs, I found that the Reverse Lookup Zones folder was empty.

## Plan of Action
1. Created a new Reverse Lookup Zone.
2. Added a Pointer (PTR) record in that zone pointing to the DC.

![Reverse lookup zone and PTR record](screenshots/)

## Validation
On the client, I ran `nslookup yourdomain.local` and it returned the DC's name.

![nslookup result](screenshots/)

## Documentation
There was no Reverse Lookup Zone, so `nslookup` could not return the server name. I created a Reverse Lookup Zone and added a Pointer record for the DC to fix it. Since this is a virtual lab, turning the server off constantly might have corrupted a file or caused issues with the lookup zone configuration.
