API Design and Pragmatic Python
================================

A talk given by [Kenneth Reitz](http://kennethreitz.com/) at PyCodeConf 2011.


Outline
------------------

- Bio
    - Work
        - Readability
        - Reflog
        - Worked on Changelog
    - Projects
        - Requests: HTTP for Humans
        - Tablib: Pythonic tabular datasets
        - Legit: Awesome git interface
        - OSX-GCC-Installer: Angers Lawyers
        - Clint: CLI tools
        - Envoy: Subprocess for Humans
        - Httpbin.org: Requests and Response service
- Philosophy - Python for Humans
    - Want to share your favorite parts?
    - We share a dark past - PHP, Perl, ColdFusion
    - The Zen of Python - PEP20
        
        ```python
        import this
        ```

- Live code demo playing with GitHub API
    - Demonstrate Ruby solution - fairly clean
    - Demonstration of Python's shite HTTP interfaces
        - Same request in Python requires ~45 lines of code
    - Admit it - if you saw this as your first experience in Python, you'd leave and never come back
- The Problem
    - It is not clear which web module we should use
    - Documentation is crap
    - HTTP should be as simple as the print statement
- The Solution
    - Python needs more pragmatic packages
- HTTP breakdown
    - A small set of methods with consistent parameters
    - They all accept headers, url parameters, and data
    - urllib2 is toxic
    - How Requests solves this issue
    - Litmus test - is it simple?
    - The API is all that matters   
- Example of Subprocess
    - Does anyone use it? - Power, effective and second worst API ever
    - Documentation is severely lacking
    - The main subprocess object takes 20 different arguments
    - High barrier to entry
    - Proposed Solution - envoy
    - subprocess is blocking devops folks from adopting Python
- Barriers to Entry
    - Installing Python on OSX has too many options
        - Download installer?
        - 32 bit or 64 bit
        - Build from source?
        - Unix or framework build
        - There should be one way to do it - don't have that now
    - XML
        - etree is terrible
        - lxml is awesome, but difficult to install
    - Packaging and Dependencies?
        - pip or easy_install?
        - setuptools isn't included in Python?
        - Distribute is awesome, but why use it?
        - No easy_uninstall
        - "Released" packages not in the Cheese Shop
    - Date[time]s
        - Which module to use?
        - How to handle timezones?
        - The stdlib can generate but not parse ISO8601 dates
    - unicode
        - It's an easy problem to solve - [NO IT'S NOT](http://bnter.com/convo/44897)
    - Proposed solution: [The Hitchhiker's Guide to Python](http://docs.python-guide.org/en/latest/index.html)
- The Manifesto
    - Simplify terrible APIS
    - Add to our documentation


Questions
-------------------

- What other modules do you think needs a full rewrite?
    - I don't think we should rewrite - we should add a new module that wraps the poor API.
- I like the idea of the Hitchhiker's Guide, but do you see any scenarios with conflicting strategies (e.g. enterprise vs. web)?
    - I don't think there should be one way to do absolutely everything.  I think those scenarios should be included in the guide.


References
-------------------

* [Blog](http://kennethreitz.com/)
* [Twitter](http://twitter.com/#!/kennethreitz)
* [GitHub](http://github.com/kennethreitz)
