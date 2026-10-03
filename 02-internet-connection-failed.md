# Issue 2: Internet Connection Failed

**Environment:** Oracle VirtualBox v7.2.8 / Windows Server 2019 / Windows 10 Pro

## Issue
The client computer cannot connect to the internet.

## Diagnostics
I ran `ipconfig /all` to check whether the client had a valid IP address. The client had an APIPA address.

## Probable Cause 1
The client computer could not establish a proper connection to the DC.

## Testing Theory 1
As an admin, I ran:
- `ipconfig /release`
- `ipconfig /renew`
- `ipconfig /flushdns`
- `ipconfig /registerdns`

**Result:** `systeminfo` showed the client was now connected to the domain `mydomain`, and `ipconfig /all` showed a valid IP address, but there was still no internet connection.

## Probable Cause 2
The network information was cached and not able to update.

## Plan of Action
In network settings, I performed a network reset.

**Result:** The computer regained network connectivity.

## Validation
Opened a web browser, went to YouTube, and played a video.

## Documentation
The networking configuration was cached and no longer receiving the correct information to connect to the internet. A network reset fixed the issue.
