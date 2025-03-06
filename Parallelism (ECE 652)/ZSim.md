# ZSim: fast and accurate microarchitectural simulation of thousand-core systems.

Daniel Sanchez and Christos Kozyrakis.
SIGARCH Comput. Archit. News 41, 3 (June 2013), 475–486. 
https://doi.org/10.1145/2508148.2485963

# Summary

At the time of this paper, simulators for very many cores are either too slow or too inaccurate. Furthermore, there are more and more systems that are present in the real world that run thousands of cores, yet there is very little out there that can simulate these systems to study them. ZSim aims to bridge this gap and provide an accurate and fast simulator for these massively parallel systems.

Speedup is achieved via 3 main techniques - 

(1) Instruction-driven timing models with dynamic binary translation. The simulator makes use of instrumentation (ie running the functional validation on the actual hardware present, requires the same ISA) to massively speed up simulation time. There are also optimized implementations of in order and OOO, which do instrumentation based simulation in batches and don't need to store microarchitectural state, just the cycles for execution (which is a massive speed boost).

(2) Bound-weave scales parallel simulation without significant overheads or loss of accuracy. The insight here is that at a small timescale of around a 1000 cycles, most concurrent accesses happen to unrelated cache lines. Therefore you can simulate around a 1000 cycles approximately first and then "fix" the timing errors later which is much more performant. This is done using a bound (do functional things) and weave (fix any timing issues) phases.

(3) The simulator is also designed to allow applications to be easily simulated for a large number of cores since there are not commonly used benchmarks or OSes that support this. This is a custom user-level simulation implementation that allows for easy simulation of many cores that still provides a lot of useful insight.

This simulator is then compared to real hardware (intel westmere) and it is shown that the simulator is pretty accurate (perf is within around 10%), however, what is more relevant is the relative performance gain of different configurations which seems to scale well (however the contention model could still be better).

# Strengths

- I thought this was technical genius. There are so many cool optimizations made here in order to make this simulator performant and still accurate.

- I thought the idea of using instrumentation to speed up simulation and then not needing to store any architectural state was so amazing.

- This paper has also shown me how hard simulating things actually is, it's basically re-creating a system all over again and the amount of details you choose to model is really a tradeoff between speed and accuracy that I hadn't quite appreciated before.

- Again, a lot of the relative time-ordering things were very awesome optimizations.

# Weaknesses

- I found this paper a bit hard to read, I think there were just so many hard concepts thrown about due to the nature of the paper that it was difficult to keep track of everything. I think some more clear cut examples with simpler systems and then building up to complex cases would have been nice.

- Figure 6c seems to suggest that the simulator's contention model actually exponentially gets further away from real hardware as the number of cores increases and thus even extrapolation would imply that their simulator is not very accurate for very large core counts. This seems like a big issue?

# Questions

- First question is to do with last weakness - the data does not seem to suggest that this will be a good simulator with contention for massive core counts.

- I'm curious why using performance (1/time) is better than IPC for multicore? 

- How were they able to model the Westmere core so well? I thought that most companies like intel guarded their architectures very closely, and they seemed to have essentially reverse engineered this architecture with ease if they did not have access to its specs already.`