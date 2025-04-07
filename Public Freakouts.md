---
Author: Anthany Martin
Deck: [Red Canary, DenSecure, Core V2.2]
---

# solution

![solution](https://github.com/4kmartin/Backdoors-and-Breaches-Scenarios/blob/main/_assets/public.png)

## Initial Compromise

Jen Barber put a USB WIFI antennae in her workstation and connected to the guest network to bypass the DNS filter so she could listen to Spotify.

Jen is also hosting an SMB file share on her PC that is configured with anonymous login. She uses this to transfer files from her desktop to her personal laptop so she can work at home.

The Threat Actor abused this connectivity to take over her machine and bounce from the guest network to the corporate network.

## Pivot and escalate

the threat actor dumped the LSASS and got the password for the helpdesk local administrator. 

This local admin has access to a config that contains a helpdesk tech's (John Moore) credentials.

## C2 and Exfil

The threat actor is able to login to the helpdesk remote administration software using John Moore's credentials

## Persistence

The threat actor uses the remote administration software to create a local admin on all devices in the network

# Initial prompt

The SIEM creates an alert notifying the SOC of multiple failed logins from the same source IP.

If the players ask to resolve the IP they will find it points to a Windows Desktop PC that is assigned to Jen Barber

if the players ask what credentials are showing the failed logon: it is the Help Desk's local admin

