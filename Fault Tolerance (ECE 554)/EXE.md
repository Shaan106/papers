# EXE: automatically generating inputs of death
Cristian Cadar, Vijay Ganesh, Peter M. Pawlowski, David L. Dill, and Dawson R. Engler.
In Proceedings of the 13th ACM conference on Computer and communications security (CCS '06). 
Association for Computing Machinery, New York, NY, USA, 322–335. https://doi.org/10.1145/1180405.1180445

## Summary

At the time this paper is written a lot of bug finding is either static analysis (which misses all runtime information), or manual via code review or contrived testcases. EXE is essentially a tool which uses dynamic symbolic execution to catch bugs in code that aren't easily caught by other methods. The high level idea is as follows: (1) Define which parts of your code can be symbolic (ie things with unknown or unbounded values), (2) run the code with these symbolic values, applying constraints over the execution for what values of the symbolic variables are allowed where in the execution, (3) if these constraints are violated, then you have a bug (you can continue executing with that range of values not allowed to catch future bugs too, although they could now be masked if you change the meaning of the code).

The idea here is to make a program that tries to actively generate cases that break another program rather than randomly testing it and hoping it breaks.

### Strengths

- Really, really good explanations. I was a big fan of the language used and also the commented code diagrams, helped me understand the paper much better.

- Optimizations were cool.

- I think I especially like ideas like this which are simple conceptually but do really awesome things.

### Weaknesses

- I can imagine the runtime for this grows exponentially, how does this compare against static analysis/random testing in very large codebases?

## Questions

- It seems through there example once you find a bug you can continue to run the code with an added constraint for whatever caused that bug. This seems to me like it could mask future bugs? As in imagine i != 0 constraint is added because of a div by 0, then later in the code if there is another potential div by 0, it would be masked by the previous constraint. This seems silly as this just seems like a speedup optimization rather than helpful for bug finder.

"evil packets" funny