BSides ATX 2019 Talk
"Miter"
ARTHIR

Michael Gough, co-founder
IMF Security
Log-MD

Podcast: Breaking Down incidient response


He's an incident reponse
- requires you to be self-sufficient in your tools
- you can't install a bunch of stuff, or bring up a bunch of things on the network
- already on Windows systems
- using what is already included on the Windows systems (living off the land)

Requirements
- no GUI, those require fat clients, all CLI
- want to run larger jobs
- schedule jobs that can run things regularly

- domain attached
- *don't want to install anything*
- PowerShell v5 is the only good way to get good PowerShell logging

There are certain situations where *you can't re-image*
- i.e. environment with 100-150 servers (you can't re-image all of those)
- you *must* fix what you have

Arthir
- this tool we're going to use
- it leverages Powershell

MITRE ATT&CK
- it's a great place to map your hunts
- if you can detect and/or hunt for the techniques in MITRE ATT&CK...you are WAY ahead of most
- the 'A' in ARTHIR is for ATT&CK

Fill out an ATT&CK Matrix

'R' in ARTHIR is for remote
- hunt and reponsd remotely

'TH' in ARTHIR is for Threat Hunting

'IR' in ARTHIR is for Incident Response
- need to respond to an attack
- push stuff via SCCM

Modularity
- uses the KANSA framework

there isn't very good documentation for KANSA

There's dozens of modules, premade templates, etc.
Some modules were ported from KANSA too
Everything ran gets moved from C:\Windows to somewhere else you specify
Script start/end time are included so you know after the initial test, if something takes 3 min or 3 hours

You and the bad guys use Powershell
So test and whitelist the scriptblocks that ARTHIR creates
- make it easier to hunt the bad




google:
Malware Archaeology Cheat Sheets
BigFix (a tool? or was he talking about some large generic "tool" provided by some IT dept.)
SANS THIR talk in NOLA?

ARTHIR is a massive improvement to KANSA


This type of incident response is what the test engineers at NSS Labs use to create a report
showing how well/bad products did at detecting malware actively working against them.