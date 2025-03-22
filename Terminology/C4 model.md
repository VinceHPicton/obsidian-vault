The 4 Cs are:
- **Context** - how users interact with each entire system, and surrounding systems that aren't yours - for example, users, the bet365 app, the banking systems it interacts with
	- An entire internet banking system

- **Containers** - Zoomed in context system - roughly speaking this is an independently deployable piece of a system, the lines between containers will be **network calls** examples: 
	- a database
	- mobile app
	- web app
	- web backend
	- Shell script
	- A lambda

- **Components** - zoomed in container - components form the parts of a container, such as: 
	- An Email component (SES, or a set of Java classes)
	- Sign in controller (cognito?)

- **Code** - rarely used - it's a zoomed in component - the specific classes, enums etc.