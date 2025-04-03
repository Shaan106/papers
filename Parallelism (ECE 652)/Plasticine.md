# Plasticine: A Reconfigurable Architecture For Parallel Patterns

Raghu Prabhakar, Yaqi Zhang, David Koeplinger, Matt Feldman, Tian Zhao, Stefan Hadjis, Ardavan Pedram, Christos Kozyrakis, and Kunle Olukotun. 2017. Plasticine: A Reconfigurable Architecture For Parallel Paterns. In Proceedings of the 44th Annual International Symposium on Computer Architecture (ISCA '17). Association for Computing Machinery, New York, NY, USA, 389–402. https://doi.org/10.1145/3079856.3080256

## Summary

People want more compute from their processors. Normal processors don't accelerate specific algorithms well enough, ASICs are too expensive (and take a while to develop) and FPGAs spend around 60% of their area on reconfigurability. Plasticine is a coarse-grain, reconfigurable fabric with direct architectural support for parallel patterns. It is highly efficient in terms of area, power, and performance and easy to use in terms of programming and compilation complexity. Plasticine addresses these challenges by specifically targeting parallel patterns like map, reduce, filter, and flatMap.

The architecture consists of two main components: Pattern Compute Units (PCUs) and Pattern Memory Units (PMUs). PCUs are multi-stage pipelines of reconfigurable SIMD functional units that efficiently execute nested patterns, while PMUs contain banked scratchpad memories with configurable address decoders that exploit data locality. These units communicate through a pipelined static interconnect with separate data and control networks.

The evaluation shows that Plasticine achieves up to 76.9× improvement in performance-per-watt over a conventional FPGA across a range of dense and sparse applications. Plasticine also has an area footprint of 113 mm² in a 28nm process and consumes maximum power of 49W at 1 GHz clock. The architecture successfully balances flexibility and efficiency by providing architectural support for parallel patterns at a coarse granularity.

## Strengths

- I thought the breakdown into very distinct parallelizable components was a really neat insight (a way in which I hadn't thought about approaching parallelism before).

- Big fan of the diagrams and really good evaluation, overall one of the most fun papers to read in terms of ideas presented.

- I am also a big fan of papers like this where problems are approached more so from the ground up, it feels like there is more room for innovation and completely new ideas like this.

## Weaknesses

- The approach requires applications to be expressed using their specific parallel pattern programming model, which may require significant code restructuring.

- Maybe some metrics around the usability of their high level tool would have been interesting to see. I can't imagine it is trivial to translate from something like python or C to their programming language (wheras FPGAs have a lot of HLS tools).

- How Plasticine handles irregular applications or those that don't fit neatly into parallel pattern abstractions.

## Questions

- The parallel patterns seem to borrow a lot from functional programming paradigm - why is this? Is functional programming easier to parallelize?

- How does the compilation time for Plasticine compare to FPGAs? The paper mentions it takes "minutes" versus "hours" for FPGAs, but more precise metrics would be helpful.

- Would love to see some code snippets.
