# monosat

## MonoSAT
- [MonoSAT](http://www.cs.ubc.ca/labs/isd/Projects/monosat/)
> MonoSAT is a SAT Modulo Theory (SMT) solver for monotonic theories over Booleans and bitvectors. It supports reasoning about a wide set of graph properties, including reachability, shortest paths, acyclicity, minimum-weight spanning trees, and maximum s-t flows. It also has some support for geometric predicates, in particular, for detecting intersections of convex-hulls of point sets, and experimental support for reasoning about finite state machines.
- [sambayless / monosat](https://github.com/sambayless/monosat)
- [sambayless / linedd](https://github.com/sambayless/linedd)
> linedd is a simple delta-debugger for line-oriented text files. You can use it to minimize error-causing inputs to programs while preserving those errors (making it easier to debug your code).

## Installation
### Building
- `git clone git@github.com:sambayless/monosat.git`
- `cmake .`
- `make`
	- `sudo apt-get install libgmp-dev` if `fatal error: gmpxx.h: No such file or directory`
- `sudo make install`
### Installing the Python Library
- `cmake -DPYTHON=ON .`
- `make`
- `sudo make install`
### Installing the Java Library
- `cmake -DJAVA=ON .`
- `make` => `monosat.jar`
- To use MonoSAT from Java, you will need to include `monosat.jar` in your classpath.
- You will also need to ensure that Java can find MonoSAT's dynamic library, for example:
	- `java -Djava.library.path=path/to/libmonosat.so -cp path/to/monosat.jar mypacakge.MyMainClass`

## Tutorials
- [Tutorial in Python](https://github.com/sambayless/monosat/blob/master/examples/python/tutorial.py)
- [Tutorial in Java](https://github.com/sambayless/monosat/blob/master/examples/java/Tutorial.java)

## Source Code
- [Source Overview](https://github.com/sambayless/monosat#source-overview)