# Synchronization and communication in the T3E multiprocessor.
Steven L. Scott. 1996. 
SIGPLAN Not. 31, 9 (Sept. 1996), 26–36. 
https://doi.org/10.1145/248209.237144

## Summary

The Cray T3E multiprocessor is a shared memory system scalable to 2048 processors. The T3E is the successor to the T3D, and incorporates several architectural improvements based on lessons learned from that system. The key innovation in the T3E is the addition of E-registers which are a set of 512 user and 128 system managed external registers add to the interface of the underlying processors.

E-registers are the foundation for all remote communication in the T3E. They provide a very pipelined interface to global memory that allows dozens of requests per processor to be outstanding at the same time. These registers allows the T3E to offer a set of atomic memory operations and flexible user-level messaging. The system also features virtual hardware barrier networks that can be embedded into the 3D torus interconnect.

The T3E builds upon the T3D but maintains the shared address space and 3D torus network architecture from the T3D. It simplifies remote memory access by consolidating multiple mechanisms into the E-register approach, improves remote load bandwidth, and makes specialized hardware features more flexible by moving them from dedicated hardware to normal user memory. Performance measurements show significant improvements in memory access pipelining, atomic operations, messaging, and synchronization compared to software-based approaches.

## Strengths

- The E-register is a really cool idea extending the processor's address space and increasing memory pipelining is pretty cool

- Moving from dedicated hardware resources to normal memory addresses makes resource management much simpler for the OS and users.

## Weaknesses

- I found this slightly hard to read. Maybe it's just and older paper.

- The memory model seems to be hard to reason about. I think it might be a little too complicated from the programmer's perspective.

## Questions

- Curious about the power consumption of the T3E compared to general-purpose systems with similar compute.