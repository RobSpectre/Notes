Backbone.js + Django
======================

Talk given by Leah Culver from Convore, PyCodeConf 2011


Outline
-----------------------

- Intro
    - Works at convore
    - Worked on a app for Django Dash 2009 called Leafy Chat
    - Screenshot for web app that uses IRC
    - [Grove](http://grove.io) - IRC for your company
- Chat UIs compared
    - Leafy Chat - pure Javascript
        - Minimal library usage - jQuery only
        - Message send - includes HTML in the JS
        - Four steps for message submission
             - Handle form submit
             - Create new message
             - Display message in List
             - POST message via AJAX        
    - Grove - using backbone
        - Same interface - better code
        - Based on backbone.js
        - Provides MVC for your JS
- Tips
    - When using Backbone, need to be careful about stomping on your Django templating
    - include_raw is helpful
    - Sync: default AJAX behaviors by specifying in your models a specific URL
    - Backbone always POSTs as JSON data - decode in Django with simplejson
    - Events: you can bind functions to any event (e.g. Model change, message added, etc)
    - Router: pretty cool because they support push state, can add function for these events


Questions
---------------------

- What was the ratio of JS to Django code in Grove?
    - One Django view - 10x that in JS
- Does it bother you as a Django developer that your app is now a JS app
    - I think this is the way things are going in the future. There is a trend that they will be a little more realtime.


References
----------------------

* [Blog](http://leahculver.com/)
* [Twitter](http://twitter.com/#!/leahculver)
* [Convore](https://convore.com/) 
