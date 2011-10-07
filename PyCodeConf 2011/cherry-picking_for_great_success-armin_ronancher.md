Cherry-Picking for Great Success
==================================

A talk about Armin Rocher given at PyCodeConf 2011.


Outline
-----------

- Intro
	- Consider Twitter
		- 2006: off-the-shelf RoR, static HTML, basic XML API
		- Now: The API is the service the website itself is a JS frontend to; everything is rate-limited; Erlang/Java
	- Does Ruby Suck?
		- No it does not
		- Neither does Python
		- Ruby / Python are amazing for quick prototyping
		- Expect your app to change with the challenges of the problem
- Proposed solution
	- Build smaller apps
	- Combine these apps together in a large one
- Cross Boundaries
	- Pygments is awesome - I need Pygments for Ruby
	- Choices
		- A: Rewrite pygments in Ruby
		- B: Use different syntax highlighter
		- C: Accept Python as the language for pygments
	- X only does Django
		- Do not import X
		- Store X on a class instance
		- Pass X as a param
		- make X as specific as possible
		- But not more than it has to be
- Protocol Examples
	- Awesome feature of Python
	- Flask's Views
		- Views can return response objects
		- Response objects are WSGI applications
		- No typecheck!
		- Return any WSGI app
		- Flash can return any WSGI app - e.g. return a Django app
	- Difflib
		- difflib does not need strings, it works on anything that is iterable
		- "X" == hashable and comparable
		- As specific as possible, but not too restrictive
- Interface Examples
	- Serializers
		- Pickle, phpserialize, itsdangerous, json
		- Within the compatible set of types, they all work as drop-in replacements for each other
		- Same interface
	- Loosely coupled pieces of code that work together build huge apps
	- Mergepoints
		- WSGI
		- HTTP
		- ZeroMQ
		- Message queue
		- A datastore
		- JavaScript
- WSGI
	- Pros: Every Python framework speaks it
	- Cons: only works with Python, often insufficient
	- The WSGI env:
		- Apps that need request data can limit themselves to the data in WSGI env
		- That way they are 100% framework independent
	- Middlewares
		- Often overused
		- Helpful with debugging, profiling, dispatching to different applications
		- You can wrap a Flask, Bottle and Django application to all share the same user data
- Zero MQ
	- Not a queue
	- Easier to use than HTTP
	- On the plus side you can dispatch any message to subscribers
	- ZeroMQ hides connection problem
- Message Queues
	- It might take a while
	- Move long tasks there
- Datastore
	- Classic example 
