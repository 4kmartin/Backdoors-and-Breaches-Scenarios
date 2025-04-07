---
Author: Anthany Martin
Deck:
  - Trimarc
  - Red Canary
  - Huntress
  - Core V2.2
---

> Note: In this scenario, the objective of the attacker is to create a botnet for use in future attacks

# solution
![solution](https://github.com/4kmartin/Backdoors-and-Breaches-Scenarios/blob/main/_assets/brit.png)


## initial compromise

John Moore, a new service desk tech, finds a nifty chrome extension that enables you to turn any webpage into a nicely formatted PDF. Complete with cover pages, images, and ads being removed. He finds the extension so useful that he decides to start installing it on all computers VIA GPO.

This extension contains a malicious JavaScript code that executes commands delivered from an unknown Network of C2 Servers 

## pivot

the extension begins its attack by disabling Windows Defender, and creating exceptions so that its future activity is unnoticed.  it then installs itself to the local machine, so that if the browser extension is removed it still can be compromised.

## C2

the Malware obfuscates its C2 server locations by using specially formatted comments on Britany Spears' Instagram. These comments decode to a bit.ly address that resolves to the C2 server's URL 

## Persistence

the malware then creates a logon script that simply reinstalls the malware locally if it disappears.

# prompt

Help Desk has been investigating an issue where windows defender is being completely disabled on all computers. They have reenabled it only to find it getting disabled the next day.

The GPOs are inspected to make sure a conflict is not the issue.

No Server is experiencing this issue.

A reimage of an affected PC seems to fix the problem initially but soon it begins again.

# inspiration
[Brittney Spears as C2](https://www.bleepingcomputer.com/news/security/russian-state-hackers-use-britney-spears-instagram-posts-to-control-malware/)
