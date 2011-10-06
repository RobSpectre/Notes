Processing Firefox Crash Reports with Python
=============================================

A talk given by [Laura Thomson](http://www.twitter.com/lxt).


Outline
----------------------

- Intro
    - Mozilla takes crash reporting very seriously
    - Performance graphing
    - Localization
    - App Updates
- The Basics of Soccoro
    - Named after a large antenna array in Mexico
    - People are very sensitive to the crashiness of browsers
    - [Visualation of crashes per 100 users](http://crash-stats.mozilla.com)
    - Architecture
        - web.py collector app running on Apache
        - Crash mover writes it to a NoSQL dbase on HBase
        - Processor writing metadata into Postgres
        - Middleware
        - Webapp for visualizing it
    - Lifetime of a Crash
        - Raw crash submitted by user via POST (JSON + minidump)
        - Collected to disk by collector
        - Moved to Hbase by crashmover
        - Noticed in queue by _monitor_ and assigned for processing
        - Processor spins off stack walk
        - Stack walk reuinites raw crash with symbols to generate the stack
        - Processor geneerates a signature and pulls out other data
        - Processor writes processed crash back to HBase and to PostgreSQL
    - Cron jobs
        - Calculate aggregates: Top crashers by signature, URL, domain (most crashes happen on Farmville)
        - Process incoming builds from ftp server
        - Match known crashes to bugzilla bugs
        - Duplicate detection
        - Match up pairs of dumps (OOPP, content crashes, etc)
        - Generate extracts in CSV form for engineers to analyze
    - Middlware
        - Trying to move all data access here
        - Still some queries in web app
        - Enable other front ends to data
        - In upcoming version each component will have its own API for status and health checks
    - Webapp
        - Hard part here: how to visualize data from four build channels
        - Getting a rewrite to Django
- The Numbers
    - Implementation details
        - Python 2.6
        - PostgreSQL 9.1 and some stored procs
        - memcache
        - Thrift for Hbase access
        - HBase we use CDH
    - Scale
        - Different kind of scaling: <100 users, several terabytes of data
        - The law of scale: the bigger you get, the more spectacularly you fail
        - 2300 crashes per minute
        - 2.5M crashes per day
        - Median crash size is 150k, max size 20MB
        - ~110TB stored in HDFS (3x replication, ~40TB of HBase data)
    - What can we do?
        - Does betaN have more null signature crashes than other betas?
        - Analyze differences between Flash versions x and y crashes
        - Detect duplicate crashes
        - Detect explosive crashes
        - Find "frankeninstalls"
        - email victims of a malware crash 
    - Implementation
        - >115 physical boxes (not cloud)
        - now up to 8 devs + sysadmins + QA + Hadoop ops/analysts
        - Deploy approximately weekly but could do continuous if needed
- Managing Complexity
    - Development process
        - Fork
        - Hard to install: use a VM
        - Pull request with bugfix/feature
        - Code review
        - Lands on master
    - Deployment process
        - Jenkins polls github master
        - Jenkins runs tests, builds a package
        - Package automatically picked up and pushed to dev
        - Wanted changes merged to release branch
        - Jenkins builds release branch, manual push to stage
        - QA runs acceptance on stage (Selenium / Jenkins)
    - Protip: build all the machinery for continuous deployment even if you don't want to deploy continuously
    - Configuration management
        - Some releases involve a configuration change
        - These are controlled and managed through Puppet
        - Again, a single line to change config the same way every time
        - Config controlled the same way on dev and stage; testing the same way; deployed the same way
    - Virtualization
        - You don't want to install HBase or Hadoop
        - Use Vagrant to set up a VM
        - Use Jenkins to build a new Vagrant VM with each code build
        - Use Puppet to configure the VM the same way as production
        - Tricky part is still getting the right data
- Upcoming
    - ElasticSearch implemented for better search including faceted search, waiting on hardware to pref it on
    - More analytics: automatic detectin of explosive crashes, malware, etc
    - Better queuing: looking at Sagrada queue
    - Grand Unifed Configuration System

Questions
------------------

- Pretty critical service - when you deploy, do you have a system to handle zero downtime?
    - Yes, it is a rolling deploy.  We deploy to a process, restart it and wait for it to register itself.  Everything is testing in staging and we also have the ability to roll back.  Load testing is also part of the staging process.
- Does Firefox crash if it can't submit a report?
    - No - mobile is a good example of this.

References
------------------

* [Blog](http://www.laurathomson.com/)
* [Twitter](http://twitter.com/lxt)
* [Mozilla](http://www.mozilla.org/)
