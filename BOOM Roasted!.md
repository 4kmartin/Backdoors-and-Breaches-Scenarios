---
Author: Anthany Martin
Deck:
  - Red Canary
  - Core V2.2
  - DenSecure
---

# solution

![solution](https://github.com/4kmartin/Backdoors-and-Breaches-Scenarios/blob/main/_assets/roasted_solution.png)

## initial compromise

John Moore, an accountant with the company, downloads an open source excel macro that is well known and used commonly in the industry for generating reports. The maintainer of this macro has not been online in many years, and his GitHub account credentials were exposed in a breach. This has allowed the Threat Actor to take over his account and update the macro with seemingly benign code.

the compromised macro includes  some base64 encoded text files, that translate to PowerShell commands when decoded. 

>[!info] For Example
> `powershell -encodedCommand "VwByAGkAdABlAC0ATwB1AHQAcAB1AHQAIAAnAEgAZQBsAGwAbwAgAFcAbwByAGwAZAAnAA=="` will output `hello world`

it uses these commands to assemble and run the actual malware.

## pivot & escalate

The malware dumps a list of SPNs on the network and requests tickets for all of the domain users with associated SPNs. 
It attempts to crack these Service Tickets until it finds the password for `oracle_svc` which is a member of `Domain Admins`

![boom-roasted-the-office.gif](https://github.com/4kmartin/Backdoors-and-Breaches-Scenarios/blob/main/_assets/boom-roasted-the-office.gif)

## c2 and exfil

The malware then uses BITS to transfer the `ntds.dit`, the oracle database, and contents of file shares to the Threat Actor's webserver.

## persistence

the malware gets the NTLM hash for the `krbtgt` account. It uses this access to request a golden ticket.


# initial prompt

Edith Hughes, the oracle database admin, reports she has noticed some strange login behavior for the `oracle_svc` accounts.

No failed sign in events are logged for that user.

It has logged into several locations that are out of the ordinary, such as file shares having nothing to do with the oracle database.

