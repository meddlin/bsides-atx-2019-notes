Getting Stuff on Attackers
John Strand
Twitter: https://twitter.com/strandjs


Create a "honeypot" domain account
- disable logon hours, or "set them to 0"
- set the password to something ridiculously long


Always try season + year for passwords
- when do they change? every 90 days? so do the seasons
ex: Spring2017
- for some reason, this just tends to change, lol

Canary tokens
- get someone to run something by naming it: sysprep.exe, vpnsetup.exe
- create a token, gives you a token similar to your own website
	- anytime anyone spoofs your website, this little code snippet automatically informs you of the spoof
	- so you know of anyone attmepting to clone your presence
- do this to stop phishing attacks before phisihing emails even hit your email servers

You can setup VNC on the edge of your network
- convince an attacker to run it (it looks vulnerable and open)
- then hook this up to honeybadger?

If you run OpenVPN (or some VPN on the edge of the network)
- these things run pre- and post-scripts
- you can kick off PowerShell, python, etc. on the attacker's system
- even have fun with the warning banner
	- attackers don't really read the warning banner
- all of this to get a level of attribution on attackers' machines


"There's no way a real attacker would ever run your traps"
- they had over 200 hits against the bank
- 4 systems compromised on their network they couldn't detect
- thousands of hit across the world

so, can we change the way we think about threat intelligence?

Hunting is an active activity
- it's an active engagement with the environment
- automated solutions are not hunting

Focus on network threat hunting

RITA AI
https://github.com/activecm/rita
- ran against networks using 10, 20, or 30,000 hosts
- have to scale hardware, but it works
- detect the attacker's beacon to their control center
	- well you can just randomize the beacon, right?
	- ex: has anyone ever talked about their kid as a genius?
		- the parents of genius children don't act that way
		- they scarily speak about their children doing weird ways...and then pray for help, lol
	- so don't beacon like a "genius child"
- anytime this is attempted it's actually pseudo-randomness
	- they detected the "amount of randomness"
- note: all AI algorithms are not proprietary, they've been around since the 1970s

These tools will always be free
- Rita was John's mom, she requested to constantly give back
- the developers named the tool after her before she had cancer
- He even spent *more money* to get patents, to keep others from creating their own versions for cost


Google:
- Bloodhound tool
- "password spray" by "daft hack"/"dafthack"
- portspoof (tool)
	- listen on any unused port on your system
	- provide a garbage nmap scan file where there is nothing really there
	- takes an nmap scan from moments to hours
- honeybadger
- go to Shodan, images.shodan.io
	- you can see images of systems shodan was able to get a screenshot of (literal Windows desktops)

- activecountermeasures.com/free-tools/rita
- activecountermeasures.com/documents
