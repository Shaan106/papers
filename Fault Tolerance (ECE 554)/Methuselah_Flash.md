# Methuselah Flash: Rewriting Codes for Extra Long Storage Lifetime
G. Mappouras, A. Vahid, R. Calderbank and D. J. Sorin, 
2016 46th Annual IEEE/IFIP International Conference on Dependable Systems and Networks (DSN), 
Toulouse, France, 2016, pp. 180-191, doi: 10.1109/DSN.2016.25.

## Summary

- using flash cells more and more for storage
- flash cells have a limited number of programs adn erases before they break
- smaller process nodes make number of p/e until failure smaller

- for embedded systems, you want a long lifetime. Right now the lifetime of flash cells is much lower than the lifetime of the embedded systems.


- In this work, we focus on endurance codes, in which we encode datawords to codewords before writing them to the Flash, so as to extend the Flash’s lifetime.

- Two main contributions
    - previous Flash cell models are unrealistic. They assume that levels in flash cells can be easily raised if i is less than j. This is not true in practice. Flash cells in real life are more complex and less ideal. There are only certain steps between levels that are possible from a given level.
    - Our second contribution is our development of novel endurance codes, called Methuselah Flash Codes (MFC), that provide far better cost/lifetime trade-offs than previously studied codes.

- We assume that the Flash cells support what is known as “program without erase” (PWE), i.e., a cell’s value can be changed without being erased first, as long as the value is being incremented

- cosets/general: decrease storage space, so you can represent data with more bits, therefore you can write twice/more times without having to erase

- We
assume an application that requires a lifetime gain of 12 and
we compare the cost (raw capacity) of different coding
schemes, in order achieve that requirement, for different host-
visible capacity goals.

- In the end it's a capacity/lifetime tradeoff - although area not constant.

## Strengths

- I appreciated the explanation of Flash cells and how they work. Objective definitions, everyone on same page.

## Weaknesses

- I was a little confused whether results were derived from mathematical models or from simualtions and to what extent actual hardware was tested/used.

## Questions

- "a MLC’s level can be changed from L0 to L1 or L2 (but not L3)."
    - Did not see the point here? can't you just do L0->L2->L3? or L0->L1->L3? Why is this a limitation?

- transient faults here could not just cause a bit flip, but a charge to increase to the wrong level (same bit value). Then you'd need to erase to use page? Could there be additional errors becasue of this (try to write but write no longer valid because charge is saturated)?