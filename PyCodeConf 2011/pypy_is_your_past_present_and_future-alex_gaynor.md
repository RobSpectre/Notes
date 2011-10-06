PyPy Is Your Past, Present and Future
======================================

A talk given by [Alex Gaynor](http://alexgaynor.net/), PyCodeConf 2011.


Outline
------------------

- Intro
    - There are two things that go faster than C: neutrinos and PyPy
    - About ten years ago, Psycho was released as a JIT compiler for Python
    - PyPy is a Python interpreter written in Python
- Past
    - First iteration was 2,000x slower than C Python
    - Not just interested in writing Python in Python
    - Graduated to VM implementation that was 10x slower than C Python
- Present
    - PyPy can do string formatting faster than C compiler can
    - Focused on letting everyone we can know about it
    - [speed.pypy.org](http://speed.pypy.org)
    - Edge detection on video in realtime
- Future
    - Biggest inhibition for PyPy adoption is _numpy_ support - it's expected to have support soon.
    - Tooling - JIT viewer tool helps profile your code
    - Python 3 is the future
    - "Who here wouldn't throw a small party if we killed the GIL?"
    - PyPy wants to transition to software transitional memory
- Feedback
    - PyPy team wants to hear more about their usage
    - A quant firm thinks PyPy is a competitive advantage in the marketplace
    - We want to end the use of C as a the performance language of choice


References
------------------

* [Blog](http://alexgaynor.net/)
* [Twitter](http://twitter.com/#!/alex_gaynor)
* [PyPy](http://pypy.org/)
