
# Weak Ordering - A New Definition’
Sarita V. Adve and Mark D. Hill

## Summary

This paper argues that sequential consistency is great for the programmer, however it leaves a lot of performance on the table. Weak ordering is a solution to this problem, where intra-processor reads and writes are no longer guarenteed to be executed in program order. This allows for more aggressive hardware optimizations, but requires explicit synchronization instructions to enforce ordering when required.

Adve and Hill argue that the old definition of weak ordering is too restrictive and leaves a significant amount of performance on the table. For example, certain memory rollbacks violate the old definition even though they are in line with the spirit of weak ordering (where the programmer sees a sequentially consistent interface). The new definition creates a contract between the hardware and software, where the hardware is weakly ordered if it appears sequentially consistent to all software that obeys the synchronization model.

The goal is to present programmers with a sequentially consistent interface (which is simpler and easier to reason about), but the hardware can use weak ordering to optimize performance. The key is that the software constraints (the rules programmers follow) should ensure that even with weak ordering in the hardware, the system behaves as if it's sequentially consistent to the programmer. This way, the programmer doesn't need to worry about the performance-enhancing details of the hardware.

The paper gives an example through the DRF0 synchronization model that forbids data races in a program. They show how their definition of weak ordering is more generalized and can improve the performance of such a model.

## Strengths

- The paper explains what the problem with sequential consistency and need for weak ordering well. The problem with the old definition of weak ordering is also well explained.

- I appreciated the appendix with examples to objectively define what they were arguing about.

## Weaknesses

- I found their contribution to be a bit ambiguous and hard to understand at times.

- The evaluation using DRF0 model makes sense, although a few more examples would have been particularly helpful.


## Questions

- The authors claim that the "majority of programs are already written using explicit synchronization operations". Is this because of compiler optimizations or did programmers in this era write programs with explicit synchronization in mind?