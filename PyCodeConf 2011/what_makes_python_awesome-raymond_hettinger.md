What Makes Python AWESOME?
===========================

A talk given by Raymond Hettinger at PyCodeConf 2011.


Outline
------------------

- Intro
    - The question is asked without a good answer
    - You should know why your language is awesome
- Context for Success
    - License (Open Source)
    - Commercial Distros (adoption by ActiveState)
    - Zen (underlying philosophy)
    - Community (thousands of devs globally)
    - Respository of modules (PyPi)
    - Killer apps and success stories
    - Win32
    - Books and other scholarship
- High Level Qualities
    - Ease of Learning
    - Rapid Development Cycle
    - Economy of Expression
    - Readability and Beauty
        - Beauty counts because it is more fun to write in
    - One way to do it
    - Interactive Prompt
    - Batteries Included
    - Protocols - wsgi, dbapi, etc.
        - If you've learned file opening and closing once, you've learned it forever
- A bit of awesomeness

```python
# Search directory tree for all duplicate files

hashmap = {}

for path, dirs, files in os.walk(''):
    for filename in files:
        fullname = os.path.join(path, filename)
        with open(fullname) as f:
            d= f.read()
        h = hashlib.md5(d).hexdigest()
        filelist = hashmap.setdefault(h, [])
        filelist.append(fullname)
pprint.pprint(hashmap)
```

    - This was written in five minutes
    - Novices can grasp it instantly
    - How long does this take to do in C++ (the answer is: infinite)
- Why is Python awesome?
    - Indentation
        - Audacious move - very uncommon
        - It contributes to Python's clean, unadulterated appearance
        - Your program doesn't lie to you about what it does - whitespace is not the devil
	- Indentation shows programmer intent
    - Iterator Protocol
        - many iterables
        - Many ways to consume them
        - Allows you to get the Lego effect of bringing two unrelated functions able to work together
    - List Comprehensions

        ```python
        [line.lower() for line in open(filename)
                  if 'INFO' in line]
        sum([x**3 for x in range(10000)])
        ```

    - Generators
        - Easiest way to write an iterator
        - Simple syntax, only adds the _yield_ keyword
        - Remembers state between invocations - the stack including open loops and try-statements, execution point, and local variables

	    ```python
            def pager(lines, pagelen=60):
                for lineno, line in enumerate(lines):
                    yield line
                    if lineno % pagelen == 0:
                        yield FORMFEED
            ```

    - Generator Expressions
        - Logical extension of list comprehensions and generators to unify the language

            ```python
            sum(x**3 for x in xrange(10000))

            {os.path.splittext(filename)[1]
                for filename in os.listdir('.')}

            {filename: os.path.getsize(filename)
                for filename in os.listdir('.')}
            ```

    - Generators that accept inputs
        - Generators support send(), throw() and close()
        - Unique to Python
        - Makes it possible to implement Twisted's inline deferreds
        - It would be nice to write 

            ```python
            @inline_deferred
            def session(request, cleared=False):
                while not cleared:
                    cleared = yield authenticate(request.users)
                    db_result = yield database_query(request.query)
                    html = yield format_data(db_result)
                    yield post_result(html)
                return end_session() 
            ```

	- Yield is _awesome_
    - Decorators
        - Expressive
	- Easy on the eyes
	- Works for functions, methods and classes
	- Functions have always been first class citizens

            ```python
            from itty import get, post, run_itty
	    import os, subprocess

	    @get('/env/(?P<name>\w+)')
            def lookup_environ_variable(request, name):
	        return os.environ[name]

            @get('/freespace')
	    def compute_free_disk_space(request):
	        return subprocess.check_output('df')

	    @post('/restart')
	    def test_post(request):
	        os.system('restart')

	    run_itty()
	    ```

    - With statement
        - Clean, elegant resource management
        - more importantly, it is a tool for refactoring code
        - With statement is profoundly important - as important as the subroutine
        - Few languages currently have a counterpart to the with-statement
	- It allows us to change the middle of code without affecting setup and teardown

        ```python
        with locking:
            access_resource()
        ```

     - Abstract base classes
        - Uniform definition of what it means to be a sequence, mapping, etc
        - Ability to override isinstance() and issubclass()
        - Mix-in capability

            ```python
            class ListBasedSet(collections.Set):
                def __init__(self, iterable):
                    self.elements = 1st = []
                    for value in iterable:
                        if value not in 1st:
                            1st.append(value)
                def __iter__(self):
                    return iter(self.elements)
                def __contains__(self, value):
                    return contains(value)
            ```

	- Above is incomplete

Questions
-----------------

- What new PEPs are in store for you?
    - I'm working on a do/while statement

References
------------------

* [Blog](http://rhettinger.wordpress.com/)
* [Twitter](http://twitter.com/raymondh)
