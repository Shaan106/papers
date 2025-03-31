# Validating the intel pentium 4 microprocessor. 
Bob Bentley. 2001. 
In Proceedings of the 38th annual Design Automation Conference (DAC '01). 
Association for Computing Machinery, New York, NY, USA, 244–248. 
https://doi.org/10.1145/378239.378473

## Summary

Pentium 4's architecture was completely novel and "borrowed almost nothing" from previous generations. Furthermore, it was their most complex processor at the time by far. To make sure that the processor was working correctly and that it was not a money and time drain to validate Intel's team came up with a lot of innovative techniques to validate the processor.

A lot of time was spent recruiting new grads as employees, which was extremely time intensive and strenuous at first but paid off later as that team was responsible for finding most of the bugs found in the processor design. Pre-silicon validation was done using a SRTL model running in the csim sim environment. A lot of the validation (especially for floating point and instruction decode logic) used formal verification techniques. This was new at the time but effective at finding bugs that the intel team believes otherwise would not have been found pre-silicon. The team used CTEs (Cluster Test Environments) to target specific microarchitectural features to test at some point (it is too hard to control an OOO processor with just the assembly code). It also allowed testing to begin before the full chip was developed as one cohesive unit. The results were shown at the end (there is a trend of more bugs to be found with each newer generation of processor), and the breakdown of different types of bugs. Most of the bugs can be attributed to human error, but a lot were more subtle.

## Strengths

- It was interesting to see power savings being treated as a target to validate for. As in ensuring that power savings via clock gating were working as intended (which is not quite a logical bug) was an interesting perspective I was not expecting.

- I liked the observation that the previous testers could be biased as well. As in a lot of testers avoided certain kinds of tests because they thought it was time not well spent on the simulator (ie a lot of the memory exploration was left not done). The coverage caught this, but otherwise they wouldn't know.

## Weaknesses

- It would have been nice to learn a bit about what techniques they used that did not end up working.

## Questions

- What form would their formal verification models take? Would they make a mathematical model that wraps around their RTL? I'm clear with the concepts, just curious about the implementation.

- Their simulation time overall was "roughly equivalent to 2 minutes on a single 1 GHz CPU". This seems quite brief, is this enough simulation time to validate a processor (ie is this usually enough time to get into enough possible states on a real cpu)? 