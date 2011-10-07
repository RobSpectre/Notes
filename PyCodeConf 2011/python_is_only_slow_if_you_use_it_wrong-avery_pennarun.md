Python Is Only Slow If You Are Using It Wrong
==============================================

A talk given by [Avery Pennarun](http://apenwarr.ca/) at PyCodeConf 2011.


Outline
--------------

- Intro
    - Disclaimer: This does not in any way ever reflect on Google, Inc.
    - Background: bup with 80 megs/sec, sshuttle: VPN that easily handles 802.11n speeds
- How To Use Python Wrong
    - Easiest way to use Python wrong
    - A line of python code is 80-100x slower than a line of C code
    - Tight inner loops == death:

        ```python
        s = open('file').read()
        for char in s:
            ...
        ```

- The Easiest Way to Make Python Fast
    - Use regexes and C modules
    - No such thing as "100% pure Python"
    - Forget about SWiG: writing C modules is easy
    - Python + C together is so far the winning combination
    - C is simple; python is simple; PyPy is hard
- The Other Way To Use Python Wrong
    - Computation threads
        - Worthless because of the GIL
    - Threads are ok for I/O
    - fork() works great for both
    - C modules that use threads are fine
- Garbage Collection
    - Refcounting and threads - a bad combo
        - Every time I use a variable, I increase its reference count by one
        - Whenever refcount = 0, it goes away
        - Python is a mostly refcounted language
    - You would need locks around every single variable access
    - One reason why removing the GIL is almost impossible
    - There are tricks
    - Python is not a GC language
        - Demonstration with code across C, Go, Python, Java-client and PyPy
        - Demonstration with Java options - you can choose between fast or sucking up all your memory
    - Objects with mutual references never hit refcount 0
        - Python has a backup garbage collector in these circumstances
    - Getting the most out of the Python GC
        - Stay the hell away from it
        - Break circular reference by hand - most common case is trees
        - Better still: use the _weakref_ module
- Deterministic destructors
    - Quiz: does this program work on win32?

        ```python
        open('file', 'w').write('hello')
        open('file', 'w').write('world')
        ```
             
        - It does not work in win32, because you can't have the same file open twice
    - With "real" GC, you have to manage resources manually
        - files
        - database handles
        - sockets
        - locks
    - Ruffians and Vagabonds are trying to take away your deterministic destructors
        - Some people claim "real gc" is the right solution
        - "with" statement is powerful, but not good enough
- Interpreted vs. JIT
    - Hello World Benchmark (aka HelloMark)
    - Runs "hello world" twenty times
        - PyPy performs 2x slower than C Python
        - C with Valgrind is _still_ faster than Jython

References
--------------

* [Blog](http://apenwarr.ca/)
