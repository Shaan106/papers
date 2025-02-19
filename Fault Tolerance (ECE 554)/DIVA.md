# DIVA: a reliable substrate for deep submicron microarchitecture design. 
Todd M. Austin. 1999.
In Proceedings of the 32nd annual ACM/IEEE international symposium on Microarchitecture (MICRO 32). IEEE Computer Society, USA

## Summary

This paper presents a new approach to dealing with transient and permanent faults in microprocessors. The author argues that current approaches do not scale well with smaller process technologies and more complex microarchitectural designs being made. The idea is simple - have everything the untrusted processor does be sent to a trusted, less complex processor that verifies everything before allowing for the commit to happen. There are two main components to this architecture - CheckComp (check whether the execution of instructions was right) and CheckComm (check whether the communication, such as register reading, was done correctly). A watchdog timer is incorporated to ensure that forward progress continues even if the untrusted core stalls. The authors also provided some ideas for application of this design such as in self-tuned systems and to take over execution in the rare case of complete failure.

## Strengths

- I thought the self-tuned system idea was very cool, I see where the idea for the Razor paper came from now.

- Really well written, easy to understand and follow the ideas. Also clear acknowledgements of the limitations of the system, and how they will be addressed in the future (ie how much power would this take, how hard is this to formally verify etc).

## Weaknesses

- They were not particularly clear about the impacts this would have on the ROB and LSQ sizes that would be needed here, I would think because there is more latency post putting items in LSQ/ROB they would need to be larger than usual.

## Questions

- Just curious about ROB/LSQ sizes due to commit being delayed (explained above).


In the RD stage of the CHKcomm pipeline, the reg-
ister and memory operands of instructions are read from ar-
chitected storage.

it cannot detect failed or misdirected commu-
nication in the processor core. For example, if the register
renamer points an operand to an incorrect physical storage
location, or if the store forward buffers miss a communi-
cation through aliased virtual memory, coding techniques
will not detect these errors. These errors are, however, de-
tected by the CHKcomm pipeline as it re-executes register
and memory communication. Instruction fetch accesses, on
the other hand, do not need to be re-executed because the
order of accesses to this storage is not important (save self-
modifying code writes).
