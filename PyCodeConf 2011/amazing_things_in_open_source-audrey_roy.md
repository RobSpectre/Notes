Amazing Things in Open Source
=============================

A talk given by Audrey Roy at PyCodeConf 2011.


Outline
---------------

- Overview
    - Python community is a meritocracy
    - Python ecosystem patterns
    - Third party packages: Quality and quantity
    - Community building
- Meritocracy
    - Anyone can build anything
    - Anyone can start a user group
    - Anyone can be a leader as long as they put in the work
    - No permission needed
        - Issues with the way something works?  Implement whatever you want.
        - The more useful your work is, the more you succeed
    - It's fun
    - Call to action - be nice.
    - Who's in charge?
        - You run your package
    - Be careful about mailing lists - there is protocol
- Ecosystem patterns
    - What makes a Python project grow?
    - Why I use mostly Django?
        - Many third party packages
        - not having to write everything myself is fun
    - Django's Reusable app structure
        
        ```
        houses/
            __init__.py
            models.py
            views.py
            urls.py
            tests.py
        ```

    - How to install an app
    
        ```python
        # settings.py
        INSTALLED_APPS += ('houses')
        YOUR_CUSTOM_SETTING = 'your value'

        # urls.py
        # add url
        ```

    - Innovations happen in third party packages, and the cream of the crop get added to core
    - Observation: packages get more popular when users can install quickly
    - Checklist for a good package
        - "Best practices" doc on how to write third party packages
        - Well-defined, easy-to-understand spec
        - Sample code
        - Active community
        - Mailing list
        - IRC channel
        - Docs
