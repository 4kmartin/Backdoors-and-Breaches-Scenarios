---
Author: Anthany Martin
Deck:
  - Core V2.2
  - Red Canary
  - Cloud Security
  - ICS/OT
---

# solution

![solution](https://github.com/4kmartin/Backdoors-and-Breaches-Scenarios/blob/main/_assets/watchman.png)

## initial compromise

A spear phishing campaign focused on receiving department includes a malicious payload (a JS Rat that includes source code for a C# worm). John Moore, A new Hire to the receiving department attempts to download the file but it is blocked. 

A coworker mentions that they have had a similar issue and that they need to connect to the guest Wi-Fi. John Grabs a USB Wi-Fi antennae off of the training kiosk in the break room and uses it to connect the shipping pc to the guest Wi-Fi. 

When the file is downloaded and opened it opens a Webpage pretending to be a BOL. this activates the RAT, which compiles and executes the worm.

## pivot and escalate

Due to a misconfiguration of how user IAM policies are managed, the TA was able to create a new IAM policy which granted them global admin rights in the Azure AD domain.


## c2 and exfil

with the new access, the worm exports the recall databases on each infected machine and sends them to the threat actor.

## persistence

the worm also installs a process that will reinstall the worm every time [sticky keys is activated](https://help.fortinet.com/fsiem/Public_Resource_Access/7_1_3/rules/PH_RULE_Sticky_Key_Backdoor_Copy_Cmd_exe.htm)



# Initial Prompt

SOC receives several Threat Intel alerts for a destination IP that is located in Moldova. 

Virus Total shows 4/92 Security providers mark this as malicious. 

if the Defenders choose to check Threat Fox they will see that the IP was flagged yesterday and tagged as potentially Distributing an unknown info stealer malware. This IOC comes with Medium (50%) confidence

the source Ip is located in the Guests Wi-Fi and the mac appears to be randomized.



# Inspiration

Initial compromise Scenario is inspired by [PACT's Write up on Dark Watchman](https://web.archive.org/web/20220629230035/https://www.prevailion.com/darkwatchman-new-fileless-techniques/)
