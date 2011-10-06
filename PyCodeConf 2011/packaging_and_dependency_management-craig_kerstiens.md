Packaging and Dependency Management
======================================

A talk given by Craig Kerstiens at PyCodeConf 2011.


Outline
---------------

- Why It Matters
    - Rapid bootstrapping
    - Predictable behavior
    - Deployment
- Packaging
    - Tool is distutils
    - Write a setup script
    - Creating a source distribution
    - Release it
        - BUT WHERE?
- Release options
    - Your server
        - You get full control
        - People rely on your availability
        - Don't do this
    - GitHub
        - Awesome for development
        - Awesome for collaboration
        - Not awesome for release
        - Not an appropriate vehicle for release
    - PyPi - The Cheese Shop
        - Host it here
        - If it's down, the entire community knows
        - There's mirrors for a reason
- Managing dependencies
    - Old tools: easy_setup
    - New tools: pip and virtualenv
    - pip benefits
        - Supports uninstalling
        - Lots of small improvements
        - Supports version control (don't do this in production)
    - virtualenv benefits
        - Tool for creating isolated Python environment
        - Creates local sandbox of environment
        - Destroy and recreate often
- Tips for Packaging
    - Be explicit with version numbers in dependencies
    - It should be absoluting explicit - it is very easy to do
    
        ```
        pip freeze > requirements.txt
        cat requirements.txt
        ```

    - PyPi's down

        ```
        pip install --use-mirrors
        ```

- What's missing
    - Bundler
        - Gemfile
        - Gemfile.lock
    - Pip needs a cleaner upgrade


Questions
--------------------

- Why isn't --use-mirrors the default?
    - Next release it will be
- How do you handle versions of dependencies of dependencies?
    - Pip 3 will take care of this for you?  Using Pip freeze will take care of everything
- How do I use setup.py with respect to requirements.txt?
    - requirements.txt is the canonical way going forward.
- On Heroku, when you deploy, is it using requirements.txt?
    - It absolutely is - you'll always know what it is going to do on Heroku.


References
----------------------

* [Blog](http://www.craigkerstiens.com/)
* [Twitter](http://twitter.com/#!/craigkerstiens)
* [Heroku](http://www.heroku.com/)
