# Argus: Low-Cost, Comprehensive Error Detection in Simple Cores
A. Meixner, M. E. Bauer and D. Sorin 
40th Annual IEEE/ACM International Symposium on Microarchitecture (MICRO 2007), Chicago, IL, USA, 2007, pp. 210-222, doi: 10.1109/MICRO.2007.18.


## Summary

Argus is a low-cost, comprehensive error detection for simple cores. The idea is that previous techniques have too much of an overhead associated with them when it comes to error detection (and also correction), to a point where those techniques are realistically infeasible (especially for simple cores). Argus identifies 4 main components that are needed to ensure correctness in any Von Neumann processor: control flow, dataflow, computation, and memory access. The authors lay out these key concepts (and explain why this is true), and then show an example via Argus-1.

Argus-1 uses a bunch of very cool techniques that are based around invariants. They don't exactly do replication (which has a high overhead), and instead use hashing and signatures to ensure that invariants are still true. This is done through techniques such as dataflow graph generation and checking. The authors show that this technique is very effective at detecting errors, and that it has a very low overhead compared to previous techniques.

## Strengths

- I thought this optimization was really neat:
    - "storing DCS bits in unused instruction bits, which are common in fixed-size RISC instruction formats"

- I also thought it was really clever to lose the ability to detect a few cases of errors due to aliasing for performance. I thought this idea of seeing the point of diminishing returns is something that is seen not very often in fault tolerance papers we have read, but it makes more sense if you want to make this idea a real, feasible product.

## Weaknesses

- I understand it was not part of the paper, but some greater discussion on how the dataflow graphs are generated, stored (overhead because of that?) and just dealt with would have been nice.

## Questions

- What are masked vs unmasked injection errors?

- The machine code for such programs needs to be altered slightly, although it seems very systematic. Would it almost be possible to insert signatures at run time via hardware (and then have signatures statically generated implicitly by the compiler). Perhaps you could do the "checking" in parallel? Would this even be beneficial power/area-wise?
