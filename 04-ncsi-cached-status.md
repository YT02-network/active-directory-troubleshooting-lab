# Issue 4: Cached Network Connectivity Status Indicator (NCSI)

**Environment:** Oracle VirtualBox v7.2.8 / Windows Server 2019 / Windows 10 Pro

## Issue
The network icon says I am not connected to the internet, even though I can connect to a website like YouTube.

## Diagnostics
I ran `ipconfig /all` and all IP configurations were correct. The client could also ping 8.8.8.8.

## Probable Cause
The Network Connectivity Status Indicator (NCSI) was showing false information.

## Testing Theory
I opened a web browser and successfully reached YouTube, confirming the connection was working.

## Plan of Action
Because this is a virtual machine, I cycled the virtual network link:
1. In the VM menu, went to **Devices → Network → Network Settings → Advanced**.
2. Unchecked **Cable Connected**, waited a few seconds, then checked it again.

*On a physical machine, you would unplug and reconnect the Ethernet cable.*

**Result:** The NCSI now shows an internet connection.

## Validation
The NCSI shows I have internet access, and I confirmed I can still reach YouTube.

## Documentation
The NCSI was showing a faulty status, most likely a cached "no internet" state. Disconnecting the virtual network link, waiting briefly, and reconnecting it fixed the issue.
