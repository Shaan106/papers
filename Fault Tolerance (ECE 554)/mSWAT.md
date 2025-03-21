# mSWAT: Low-cost hardware fault detection and diagnosis for multicore systems
S. K. S. Hari, M. -L. Li, P. Ramachandran, B. Choi and S. V. Adve 
2009 42nd Annual IEEE/ACM International Symposium on Microarchitecture (MICRO), 
New York, NY, USA, 2009, pp. 122-132.

## Summary

mSWAT is a system which allows for very low overhead fault detection and diagnoisis in multicore systems. It builds upon the work of SWAT and takes ideas from BugNet and trace based fault diagnosis. The key idea is that during normal operation, there is low overhead fault detection always running, and only when a possible fault is detected is the fault diagnosis system invoked.

The fault diagnosis system detects a few kinds of faults: Fatal-traps (traps not thrown in normal execution that show anomalous software execution), Hangs (if a branch is being taken too often and the system is making no progress), High-OS (abnormally high usage of the OS usually indicates faults) and Panic (detects kernel panics). These are intended to be low overhead and simply flag that there is likely a problem somewhere, and hand over to the fault diagnosis system.

The fault diagnosis system works a little differently. Here, the main idea is to identify the type of error (transient or permananet) and in which core. Transients are discovered via non-determenistic replay, if the result is the same then it is likely no big deal. If it is different then there is either a software or permanent bug. Then cores are run to create a trace of their execution (this is needed for deterministic replays). The trace only keeps load instructions of its own core, since only that is needed deterministic replay. Then these traces are run on pair cores that are switched (assuming a one core faulty model). The idea here being that the replay only needs its own loads in which order with the values it recieved to recreate that trace. No inter-core communication required in deterministic replay. If the pairs of cores differ then we have an error, and the type of instruction and where it differs can be used for identification.

## Strengths

- The system really takes the make the common case fast approach, and it seems like it is easily implementable due to the low overhead of the fault detection system

- I was a big fan of figures 3 and 4 for demonstrating the cases in which the system excels. I think the diagrams did a really good job of showing how the system works.

## Weaknesses

- I was not convinced by the ways in which errors are detected. I would've liked to see more of a discussion on why this is sufficient (more in questions)

- most errors are detected within 10M instructions
    - This would seem to have a large buffer/replay overhead. Maybe this is fine since this is rare?

- What happens if the trace generation itself has bugs?

## Questions

I was confused about the selection of ways to detect errors, it seems like it has a big reliance on OS related tasks. For example what if there is a problem in the fp ALU, this seems like it would almost never detect that error to begin with and erroneous values can be easily used. 

Similarly, how likely is it to find a fault in the int divider? Seems like everything that causes an error must lead to some sort of big OS error, I don't know how likely it is in programs that a divider doesn't impact things like page faults.