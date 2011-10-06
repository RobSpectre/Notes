The Future Is Bright
========================

A talk by Jesse Noller given at PyCodeConf 2011.


Outline
------------------------

- Intro
    - The kids are alright. 
    - What is Python? "python" is the language - "Python" is the greater community
    - "On the whole, Python's community is humble - grandstanding is a distraction from getting things done."
    - "Use Python where it makes sense - and it makes sense in more places than you might realize."
- Where is Python used?
    - Short impressive goddamn list
    - It's glue and it's steel
    - Python is amazing; it is stunningly simple to use
- State of the Language
    - 123 accepted PEPs
    - 115 are "Final" status (out of 284 total)
    - 60 rejected, 21 withdrawn
    - 80 built-in functions
    - 285 documented modules inside the doctree
    - And yet it still fits in your head
- The Future of Python
    - PEPs in process: coroutines, async IO, cofunctions, daemon support, etc.
    - Python 2.7 is the end of the road for Python 2.x
    - Python should be the Borg of programming languages - continually borrow and adopt from other langs.
    - We not be insular - adopt what makes sense within the Pythonic philosophy
- Things We Should Absorb
    - Better communication systems; lightweight support
    - Add one of the event (gevent/eventlet/etc) modules to core
- Things We Need
    - Better abstractions; clean Pythonic APIs
    - No more leaks
    - "The API matters" both in code and community
    - Python is a conservative language
    - The core needs to remain simple and understandable
- Interpreters review
    - PyPy is *fast* - however there is a tradeoff.  It is complex; the interpreter doesn't fit in your head
    - C Python is the evolutionary equivalent of the cockroach - old but tough and tested
    - Predictions: in several years PyPy will become dominant, but will not unseat C Python entirely
    - All the interpreters must work together
- Python 3.0
    - Keep calm and carry on.
    - Python is 21 years old - 5 years is *nothing*
    - Try to make your codebase support both 2.7 and 3.0
    - Still a few years away from the tipping point of adoption
- Community
    - We must be welcoming
    - [Local Python groups](http://bit.ly/nwsfJV)
    - Get involved - go outside (the language)
    - Don't be a jerk
    - We're in this together

Questions
------------------------

- Is there any PEPs coming up that you're excited about?
    - PEP 380: allows you delegate to the subgenerator to have coroutines within the language.  It is advanced usage, but it is a good evolutionary step.  The async IO is going to pull the best things from Twisted and pull them into the core language.

References
------------------------

* [Jesse Noller's blog](http://jessenoller.com/)
