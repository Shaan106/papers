# Is SC + ILP = RC?
Chris Gniady, Babak Falsafi, and T. N. Vijaykumar. 

## Summary

This paper is about improving Sequential Consistency (SC) based hardware so that it can keep up performance wise to Release Consistency (RC) 
which provides no handrails and relies on the programmer to ensure programs run correctly.

The paper introduces a new hardware based model called SC++ which exploits more aggressive speculative execution at the hardware level to
have performance at a similar level to RC.

The SC++ model relies on a few tricks and assumptions:

1. load + store bypassing
2. speculative state for memory as well to allow OOO memory operations
3. hardware speculation does not massively increase processor critical paths
4. good algorithms do not need to rollback speculative execution very often

The way SC++ is abel to achieve this speedup from normal SC is by having more speculative execution. Traditionally this involves needing larger buffers
to store speculative data, for example a larger store buffer. However, this increases the critical path of the processor, leading to additional slowdowns.
In SC++ the authors propose to move the speculative memory execution to the cache itself, which allows for a precise log of memory operations for rollback.
This way the critical path of the processor is not increased, but the rollback penalty is much higher. As long as the program is "well behaved" not many rollbacks
should be needed, and thus the processor will execute much faster. However, if the program is not well behaved, the processor will have to rollback many times
and the performance will be much worse than a normal SC processor (the authors argue that this will not happen very often with well written programs).

## Strengths

- I thought the idea behind this paper was really interesting. There is a very clear re thinking of an idea to provide a new perspective on how to solve a problem.

- The paper continuously backs up every decision made with clear reasoning. It is easy to follow the logic of the authors, for example, why they thought that moving the speculative memory execution to the cache would be a good idea.

- Strong, clear results and clear analysis.

## Weaknesses

- I would have liked to see more reasoning and data behind their "well behaved" program argument. It seems like a very important part of their argument, but there is no data to back this up.

- Also, some data on the power/performance/area disadvantage of the SC++ hardware would have been helpful to see. I could see a scenario where the 
SC++ hardware is much larger and more power hungry than a normal SC or RC processor, and may even be clocked slower (and thus lose performance).

## Questions

- What are some additional security concerns with this speculative hardware? Can we execute even more malicious code now?