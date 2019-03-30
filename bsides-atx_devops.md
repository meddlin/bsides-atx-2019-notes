

you can have security tools siting between dev and ops

turn local discoveries into global improvements

DevOps practices
- config management
	- infrastructure as code
		- how can you get config into source control?
	- reproducibility and traceability come from this

- config integration
	- it can be what you make it
	- can put security checks, static analysis, or integrated pen tests
	- remember devs care about getting code out the door

- continuous delivery
	- want to deploy stuff without it being a big deal, near-0 down time
	- try "canary releases" where you push out to 10, 20, or 30% of users at a time
	- perhaps you want to know how a security change is going to affect things?
		- you have leverage to move around here, so you can test these effects down the road

Communication
- Slack -- increases communication across teams/depts. to get realtime feedback
	- email doesn't get this same level of transparency


DevOps really can be a conduit to build relationships between: software, security, & operations
- it's the Dev/Sec/Ops

these are good highlevel languages to know across tech stacks and teams
- python
- bash
- powershell
- yaml
- json
- markdown

Make use of code linters
- this can have a security lean towards it
- works really well for interpreted code, too
	- ...as you normally don't find these errors until you run the code



Google this:
- pylint
- flake8