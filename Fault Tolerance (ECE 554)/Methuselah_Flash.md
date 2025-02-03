# Methuselah Flash: Rewriting Codes for Extra Long Storage Lifetime
G. Mappouras, A. Vahid, R. Calderbank and D. J. Sorin, 
2016 46th Annual IEEE/IFIP International Conference on Dependable Systems and Networks (DSN), 
Toulouse, France, 2016, pp. 180-191, doi: 10.1109/DSN.2016.25.

## Summary

The paper addresses the limited lifespan of flash memory cells in storage systems, specifically for embedded applications where device memory lifetime is especially important. This paper puts forward the idea of Methuselah Flash Codes (MFC), an encoding scheme that extends flash memory lifetime with a better encoding (which is developed using insights from a more realistic models of how flash cells actually behave). In the end it's a capacity/lifetime tradeoff that is being optimized for.

The work presents two contributions: it develops more practical flash cell models that better reflect real-world behavior, and it introduces new endurance codes that improve the trade-off between storage capacity and lifetime. Using a program without erase approach (ie always increase flash charge level as much as possible) and coset-based techniques, the system can achieve a 12x lifetime improvement while balancing raw storage capacity requirements.

This paper differs from previous solutions by acknowledging that flash cell level transitions are more constrained than previous works assumed, and only certain level transistions are possible. Instead of treating all upward level changes as equally possible, their model accounts for the actual limitations of flash memory hardware, where only certain level transitions are feasible. 

## Strengths

- I appreciated the explanation of Flash cells and how they work. Objective definitions, everyone on same page.

- I thought the metric was very clear and easy to motivate. I could see the benefit of trying to optimize for the lifetime-capacity tradeoff.

## Weaknesses

- I was a little confused whether results were derived from mathematical models or from simualtions and to what extent actual hardware was tested/used.

- Cosets were a little confusing to me, but I think a little more time with them would make them clearer.

## Questions

- "a MLC’s level can be changed from L0 to L1 or L2 (but not L3)."
    - Did not see the point here? can't you just do L0->L2->L3? or L0->L1->L3? Why is this a limitation?

- Transient faults here could not just cause a bit flip, but a charge to increase to the wrong level (same bit value). Then you'd need to erase to use page? Could there be additional errors becasue of this (try to write but write no longer valid because charge is saturated)?