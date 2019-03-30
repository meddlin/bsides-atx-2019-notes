Privilege Escalation

Nir Yosha @niryoo
@preemptsecurity


a "threat" -- should have an intent behind it
-- notice malware or vulnerabilities don't really have this piece

common factors for auth
- something you have (password)
- something you know (smart card)
- something you are (fingerprint)

SSO - single sign-on
- allows users to access multiple services with a single login
- not necessarily password managers or auto-renewable sessions
- advantage, fast uptake and easier
- disadvantage, one key to whole kingdom
	- no single sign-off

Federated Identity (Federated Identity Management)
- a little better than SSO
- works across organizations
- allows sign-off management
- FIM gives SSO, but not SSO gives FIM
- Active Directory Federation Services (ADFS) this is from Microsoft

IDaaS (ID as a Service)
- this is Okta, Azure ID, etc.
- authentication infrastructure in the cloud

Hybrid (identity on-prem and in cloud)
- AD is on-prem, but also can sync into cloud
- ADFS is doing this, but will fade out
- Azure AD is all cloud
- this allows on-prem management, but also line of business apps with SSO

OAuth - open-authorization, token-based
OpenID - decentralized authentication protocol
SAML - Security Assertion Markup Language (this one is de-facto for cloud)

SAML stuff
- IdP identity provider
- SP service provider
- SAML assertion, these are the tickets saying the user is authenticated
- banks are running SAML against your accounts to make sure you're who you say you are

LDAP - lightweight directory access protocol, a query protocol to get AD data
- *a lot of pentest tools alter AD based on LDAP*

Also Kerberos, NTLM in this space

Kerberos
- almost like having to buy tickets at an amusement park, then having to separate tickets at each ride

Techniques to gain control
- Access system token (CVE-2015-1701)
	- win32k.sys in kernel-mode drivers
- Bypass UAC pop up window
	- auto elevate programs
	- injecting dll while running
- Injects malware into .exe
	- then dump credentials


Internal recon
- once I'm in, now where do I want to go
- techniques
	- brute force
	- service enumeration
	- account activities
	- stealthy admins

Lateral Movement
- techniques for credential theft
	- dump creds
	- guessing (based on info on individual)
	- shoulder surfing (or sticky notes)
	- brute force
	- dictionary attacks
	- security questions
	- reset passwords
- some say Win10, or Windows 2016 prevents "pass the hash"
	- but they don't...you can still dump passwords from mimikatz

Escalation tools
- BeRoot
- mimikatz
- yodo
- powerUp
- Portia
- also lookup a list of known privilege users
	- this is published by Microsoft
	- "users" to SID keys


NTLM relay
- placing a rogue target between server and domain controller
	- DCShadow fits into this, due to taking advantage of DC syncing feature

Other techniques
- pass the hash
	- mimikatz
	- psexec
- DCSync
- Kerberos related
	- pass the ticket
	- golden ticket
	- forged PAC


NTLM design flaw
- credential exposure in memory
- broken protocols still in use (NTLMv1)
- you can NOT patch a design flaw
- NTLM SSP only stores the hash for a reason
- NTLM relay has no mutual authentication
- easy to crack pwds
- no backport to Win7

Kerberos design flaw
- kerberos principles can use NTLM hashes as long-term secret keys (RC4)
- Krbtgt is the master key for all kerberos tickets (golden ticket)
	- can access to any thing in the environment at any time
- tgt tickets are portable
- priviledged attribute cert is not always inspected by DC (forged PAC)
	- forged PAC: adding services you can access because AD won't check for it
- kerberoasting

AD admin design flaw
- create similar passwords for all local admins (GPP)
- build in admin can be enabled with no UAC
- too many domain admins
- too many stale, stealthy, stolen accounts
- 3 tier approach from Microsoft
	- workstation pwd
	- admin pwd
	- domain admin/controller pwd


When a hacker/group is sitting on a network for a while
- they are gathering creds
- Black Energy (Russia) -- power grid attack
	- SCADA hack
- Lazarus

MFA solutions
- very few orgs use MFA internally because there's pushback from users
- hard to deploy and inconvenient

UBA solutions
PAM solutions

context of identity
- multimodal authentication
	- iris scans with a password
	- smart card + phone
- behavioral
	- keystroke rhythum
	- peer group comparison
	- seasonality

FIDO Alliance
NIST
firebase auth

Adaptive enforcement -- enforce more things due to the potential risk of the user




Google this:
- mimikatz
- BloodHound (enumerate services in AD)
- ekeys - to dump kerberos tickets?
- can use mimikatz to dump windows cred hashes?