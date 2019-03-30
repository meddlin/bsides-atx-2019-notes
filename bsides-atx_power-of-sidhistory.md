

Director at Protiviti

Adam Steed
-- on LinkedIn
-- he's a big influence in community and fields AD questions

Don Perez (?) -> also on LinkedIn

Stealing the password hash
- NTLM hash on box
- sent across network
- checked server-side in AD box?

Most phishing attacks are for credential theft

SIDHistory
- notice that logins actually happen with SID
- SIDHistory allows someone to essentially have multiple SIDs

There are a list of well-known SIDS
- i.e. "512" is a domain admin
- so injecting "512" into your SID is really noisy

DCShadow
-- allows you to setup a domain controller for a few minutes
- DCSync to replicate data out of AD
- DCShadow to inject data into AD
- Have you ever tried to figure out where duplications come from?
	- This is inherently difficult, which is why DCShadow is a good attack
- DCShadow is *just enough* of a domain controller to do this

Need DA rights to get into DC, normally
So, how does non-DA user log into DC?

A user has:
- regular user SID
- will turn roque machine into DCShadow
	- PSEXec -> mimikatz

	- * at this point we're preparing a package to inject
	- run command to change attribute on user account via DCShadow
		- ```lsadump```
	- then replicate this back to AD (*use your package*)

	- then removed the DCSHadow box

SIDHistory is enabled by default
We ***only want it around during a migration*** 

Most people set alerts for failed attempts
-- but who sets alerts for "successful attempts...that shouldn't happen"

Detecting DCShadow
- the DC standup and takedown is less than 5 seconds, so this is ***difficult***
- the only way we know this was DCShadow is because it didn't leave its name in the user/SID attributes
	- btw, there are thousands upon thousands of attributes *per user*
- so you can also detect this by looking for DC creation/destruction logs (in SIM roles?) a few seconds apart
- to even detect this stuff you have to turn on Advanced Auditing
	- ***This is not turned on by default***
	- This is where SIM roles are logged
- This is why you need to audit against *everyone*
	- with DCShadow anyone can be DA

Deploy 'UndercoverDCShadow'
- open source; it detects DCShadow
- you have to run this on *all* of your DCs
	- so that sucks if you have a bunch of DCs

Detect SIDHistory
- PS Scripts to compare SIDHistory to priviledged SIDs
- Document every AD Account or group that has SIDHistory
- do a comparison of what has been changed in your AD domain and that the changes have associated tickets or change requests
- *There should not just be SIDHistory changes on your domain*


Preventing this whole thing
- Microsoft ATA
- Microsoft ATP
- Preempt
- Inline IPSs (this is "intrusion prevention system"...so, very deep inside the packets)
- custom SIEM rules

Installing multi-factor auth on DC is a good way to prevent DCShadow/Sync all over the place

Some admins have the same password for their admin accounts as their regular user accounts

NOTE: With DA access, you are one script away from locking every single user out of the domain
- This then allows the attacker to ransom the entire company for a single password

Pass the Hash mitigation
If you can't run mimikatz, then you can't run a lot of this stuff
A lot of it requires local admin access
A DA should never log into a workstation
	- the DA password gets hashed on these machines
	- compromised workstation means a compromised DA password hash

Google:
NetBIOS
Responder
