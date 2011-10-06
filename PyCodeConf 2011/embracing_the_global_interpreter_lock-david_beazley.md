Embracing the Global Interpreter Lock (GIL)
====================

A talk by [David Beazley](http://twitter.com/dabeaz) on the GIL.


Outline
------------------

- Intro
    - GIL is a popular topic
    - Godwin's law of Python - the second the GIL gets mentioned, the conversation dies
    - I'm hoping this doesn't shut down the rest of the conference
- My Interest
    - It's a fun systems problem
    - Breaking GILs is my hobby
- Premise
    - Threads are useful - haters gonna hate
    - Threads make all sorts of great stuff work
    - They are being _used_
- GIL is a Nutshell
    - Python code is compiled into VM instructions
    - GIL means you can't execute those instructions concurrently
    - The GIL protects the interpreter (ref count updates, mutable types, thread safety)
- GIL issues
    - Can't use threads for multiple CPUs
    - Uninterruptible instructions
    - Bad behavior of CPU-bound threads
- The Challenge of Improving the GIL
    - It's not going to go away and it addresses a tricky problem
    - Something Python devs must embrace
    - The Experiment
      - Definition
          - A request/reply server for size-prefixed messages
          - Messaging comes up in a lot places
          - It's used for a variety of apps
      - Echo
          - Gets a message and sends it back
      - Five server implementations
          - C with ZeroMQ
	      - Unloaded: 12.8s
              - Add one CPU thread: 12.6s (same) 
          - Python with ZeroMQ
              - Unloaded: 13.0s
              - Add one CPU thread: 91.6s (7x slower)
          - Python with multiprocessing
              - Unloaded: 12.4s
          - Python with blocking sockets
	      - Unloaded: 12.7s
          - Python with nonblocking sockets
              - Unloaded: 12.2s
       - Hardware
          - XL EC2 instance
      - Test
          - 10k message
          - 8k each
     - Commentary
         - Horrifying result
         - It is not a microoptimization
         - This is a very simple example that was not a stress test
         - PyPy was 567x slower (fix already committed to trunk)
         - Python 2.7 does not have the performance penalty that Python 3.2
         - Python 3.2 GIL is supposed to be "fixed" - seems there is room for improvement
         - Trying it with a GUI program and it is still horrible
- What is going on?
    - Thread switching mechanism
        - Here's the performance problem
        - In Python 3.2, the GIL is based on a timeout mechanism
        - Any thread that wants the GIL must wait 5ms
    - The Problem
        - The 5ms starts to build up
        - CPU-bound threads significantly degrade I/O
    - Performance Explained in the Experiment
        - The messages are surrounded by waits for the GIL
        - 5ms coming and going
        - Build ups create significant delays
    - Fix is Thread Priorities
        - The original "new GIL" patch had thread priorities
        - Needs to be revisited
    - Applying the priority scheme to the previous experiment
        - Use a mechanism similar to:
        
        ```python
        import threading
        import sys
	...
	def start(self):
            sys.setpriority(-1)
        ```
        - Largely fixes the problem - 100% CPU, but GUI apps are much more responsive
        - GUI has a higher priority than your app
- Thoughts on the GIL revamp
    - We can do better
    - Introducing priority is not the only possible GIL improvement
    - Should the GIL be released on non-blocking I/O?
    - Incremental improvements can be made


Questions
---------------

- Does anyone have Python 3.2 installed on their machine?
    - No one.
- Have you written any papers on the GIL?
    - I have not written a paper on this, but there is room for a very interesting one.  There are many languages with a GIL - Ruby, Erlang also have one.  One of the things you're finding is that the languages want to do thread scheduling.  One interesting question is the thread library and OS giving the language enough help?
- The code that you have for priorities - ready for production?
    - No.  I can't get the threads to quit.  (eeeesh)


References
------------------

* [Slides](http://www.dabeaz.com/talks/EmbraceGIL)
* [Twitter](http://www.twitter.com/dabeaz)
* [David Beazley's website](http://www.dabeaz.com/)
