Attacking API Microservices
Tony Lauro, CISSP, GWAPT, GSTRT

history of api technologies
- in 2007, microservices, restful, json-based shot up

web APIs are pervasive and growing
They are a great asset to attack because of how much is touching and using them.

top threats
- denial of service
	- they are ddos'd all the time
	- could even be somoene messed up an input (legitimate user though)
	- use VDOS Stresser tool
	- https://krebsonsecurity.com/tag/ddos-for-hire/
	- attackers are also creating botnets to send traffic from home user space
		- so logging into your bank from AWS IP space should never happen (or highly unlikely)
	- crafting requests to cause hash collisions
		- deep nesting json payloads
			- can validate on JSON
				- via whitelist for what we want JSON to look like *per resource*
			- set max nesting depth, then drop request upon poor response payload formation

API Threats
- vulnerable deserializers
	- these things can be targeted before business logic is even validated/executed
- API sql injection
- JWT
	- do not store user credentials in the JWT
	- it's only a 64bit encoded string, no security


Logic Flaws
- can you validate if someone goes from step 1 to step 4? in your business logic
	- if no, then this is a high potential for a problem
- don't assume things like *only mobile apps can call the API*
- don't assume sequential numbers (i.e. for id's) always makes sense for query parameters

Other Stuff
- placing API keys inside of code snippets then hosted to github
	- gitrob is a tool to look for this
	- https://michenriksen.com/blog/gitrob-putting-the-open-source-in-osint/
	- Amazon has "git encrypt"?
	- can do these type of checks in CI/CD process
- fierce.pl is a domain discovery tool
	- domain, api, enumeration for obfuscated host names
- certificate transparency logs
	- leaving meaty words around like api-portal-development.com
		- api, portal, development are good key indicators

- API Gateways are highly recommended
	- dynamically assign and easily revoke API keys

Credential Abuse
- almost happens all the time across APIs
- API inspection can help mitigate against malicious API calls
- password dumps are feeding bad credential attempts
	- Nulled.to/forum/74-combolists
- most of the credential abuse is a request that is only made ONCE from ONE IP
	- so you get one shot
	- look at SSHowDowN

- SNIPR Account checker
	- http://reddit.com/r/SNIPR
	- can load password lists into this tool
	- also, Sentry MBA
		- has proxy and forwarding techniques


AIO bot
- all in one bots
- cyberaio -> cybersold
- dashie.io for things on shopify platform
https://www.cybersole.io/
- can create specialized access to online retail stores
- people use these tools, buy all the stock
	- causes no customers to really get the product(s)
	- customer engagement didn't happen
- you can even use these tools to pseudo-automate captchas

Pixi the OWASP project
- vulnerable API services to try your hand at





Predicting the next mega-DDoS attack -- he's currently writing this blog article
	- 3 particular ISPs in a country where people have 60+ Gb/s connections


google this:
- WireX a 0-day botnet