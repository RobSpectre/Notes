The Future of Collaboration in the Python Community and Beyond
===============================================================

A talk given by Daniel Greenfield at PyCodeConf 2011.


Outline
---------------------

- The Mark Pilgrim question
    - Mark Pilgrim has left the community
        - Dive into Python
        - httplib2
        - feedparser
        - Dive into HTML5
    - What were his projects?
        - A lot of code is gone now
        - License is permissive
        - httplib2?
            - PyPI?
            - code repo was down
            - Had to find a cached download
            - A lot of modules depend on httplib2
- PyPi issues
    - Packages are too easily deleted
        - Dependency checks missing
        - Request a handoff
        - Other projects need to be notified
        - RSS feed needed
    - Human moderation needed, but PyPI team busy
- Repeating History
    - pypants is gone
    - djangolint was gone for a while as well
    - django-piston: Google searches on REST bring up this project, but it's been two years since the last release
    - python.org: what is the status of that?  
    - opencomparison.org 
- Python's dark Future
    - Critical Package Breakdown
        - Author pulls package from PyPI
        - Breaks a number of other dependencies
        - Various build scripts fail
        - replace from caches/backups
        - Domain Knowledge is gone
        - Repercussions
            - Annonyance
            - Ability for Python to progress _halts_
            - Social issues
- Trust Issues
    - A broken package can create the impression that "You can't rely on Python"
    - Lack of trust makes collaboration hard
    - No collaboration creates the NIH plague - zombies! zOMG!
- Solutions
    - Sponsorships
        - Individual, corporate, academic, GSOC
        - Advance OSS forward
        - Problems
            - Applications are boring
            - Focus is on short-term dev
            - Work gets shifted to journeymen coders
            - Ongoing maintenance
    - Community management
        - Need core/senior developers
        - They are already busy
        - Who assigns authority?
    - PSF Paid Community Manager
        - Reasonable pay
        - Works with PyPI team to do package curation
        - Helps project leads
        - Real job: performance reviews, term limits
        - Precedents: Ubuntu, Fedora, Twilio (woo!)
- More ideas for PyPI
    - Incubation
        - Seed fund OSS project that provide ROI to Python community
        - Money via a viable business model
        - Choose participants from coding contests
        - YC-style seed funding
        - Marketing
    - Documentation
        - RTD increases trust
        - Trust increases collaboration
        - We should have a github for documentation
    - [depot.io](http://depot.io)
        - A place to freeze your Python dependencies
        - Let's PyPI focus on what it does best - indexing
        - Provides additional security
        - It's not available :(
        - PSF should incubate this project
        - Open source it
    - [PyPI](http://pypi.python.org/pypi)
        - Pay for a PyPI applicance?
    - [OpenComparison](http://opencomparison.org)
        - Compare django-registration to django-socialauth 
        - django-reg has lots of download
        - django-socialauth is obviously the hottest
        - Problem is no obvious business model


References
---------------------

* [Blog](http://pydanny.blogspot.com/)
* [Twitter](http://twitter.com/pydanny)
