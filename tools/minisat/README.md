# minisat

## Homepage
- [minisat.se](http://minisat.se/Main.html)

## Installation
- `sudo apt install minisat`

## Repositories
- [niklasso/minisat](https://github.com/niklasso/minisat/tree/master)
  - [Compilation error: Declaration of mkLit breaks compilation on OS X (with clang-503.0.40) #16](https://github.com/niklasso/minisat/issues/16)
- [agurfinkel/minisat](https://github.com/agurfinkel/minisat)
  - This fork has fixed the compilation error above.

## Branches
- [`search-tracing`](https://github.com/niklasso/minisat/tree/top/search-tracing)
- [`partial-static-order`](https://github.com/niklasso/minisat/tree/top/varorder/partial-static-order)

## Tutorials
- [MiniSAT User Guide: How to use the MiniSAT SAT Solver](https://dwheeler.com/essays/minisat-user-guide.html)
  - `minisat pre=once cnf-5-3 cnf-5-3.out`
  - It also explains how to get more solutions.
- [Python MiniSat Examples](https://python.hotexamples.com/examples/satispy.solver/Minisat/-/python-minisat-class-examples.html)
- [minisat - Man Page](https://www.mankier.com/1/minisat#)
- [niklasso/minisat-examples](https://github.com/niklasso/minisat-examples)
  - `Minumerate`: This simple example gives solutions to two frequently recurring
    encoding patterns: enumerating models and finding minimal
    models.
- [MiniSat FAQ](https://www.msoos.org/minisat-faq/)
  - Why doesn’t MiniSat find the solution to my problem that has at most 2-3 really important variables?
    - `Try lowering the random pick frequency by giving the -rnd-freq=X, setting X to be very-very low.`
  - I have a simple linear set of equations, and MiniSat cannot solve it!
    - `Try CryptoMiniSat`
- [ucacbbl/MiniSAT](http://www0.cs.ucl.ac.uk/staff/ucacbbl/minisat/)

## Cores
### [`Solver.h`](https://github.com/niklasso/minisat/blob/master/minisat/core/Solver.h)
- [newVar](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L47)
  - variable model: `bool dvar = true`
- [setDecisionVar](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L91)
  - `Declare if a variable should be eligible for selection in the decision heuristic.`
- [`vec<lbool> model`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L122)
  - ` problem is satisfiable, this vector contains the model (if any).`
- [`LSet conflict`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L123)
  - `If problem is unsatisfiable (possibly under assumptions), this vector represent the final conflict clause expressed in the assumptions.`
- [`struct VarOrderLt`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L176)
- [`vec<CRef> learnts`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L191)
  - `List of learnt clauses.`
- [`VMap<double> activity`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L196)
  - `A heuristic measurement of the activity of a variable.`
- [`VMap<char> decision`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L200)
  - `Declares if a variable is eligible for selection in the decision heuristic.`
- [`Heap<Var,VarOrderLt> order_heap`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L205)
  - `A priority queue of variables ordered with respect to the variable activity.`
- [`insertVarOrder`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L241)
  - `Inserts a variable in the decision order priority queue.`
- [`pickBranchLit`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L242)
  - `Return the next decision variable.`
- [`sovle_`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L252)
  - `Main solve method (assumptions given in 'assumptions').`
- [`varBumpActivity`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.h#L260)
  - `Increase a variable with the current 'bump' value.`

### [`Solver.cc`](https://github.com/niklasso/minisat/blob/master/minisat/core/Solver.cc)
- [`Lit Solver::pickBranchLit`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.cc#L249)
  - Random decision/Activity based decision/Choose polarity based on different polarity modes (global or per-variable)
- [`Solver::analyze`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.cc#L296)
  - Generate conflict clause/Simplify conflict clause/Find correct backtrack level
- [`Solver::propagate`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.cc#L506)
- [`Solver::solve_`](https://github.com/niklasso/minisat/blob/37dc6c67e2af26379d88ce349eb9c4c6160e8543/minisat/core/Solver.cc#L839)

### [SimpSolver.h](https://github.com/niklasso/minisat/blob/master/minisat/simp/SimpSolver.h)
### [SimpSolver.cc](https://github.com/niklasso/minisat/blob/master/minisat/simp/SimpSolver.cc)
