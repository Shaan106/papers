# Razor: a low-power pipeline based on circuit-level timing speculation
Ernst, D. and Nam Sung Kim and Das, S. and Pant, S. and Rao, R. and Toan Pham and Ziesler, C. and Blaauw, D. and Austin, T. and Flautner, K. and Mudge, T.
MICRO 2003, 10.1109/MICRO.2003.1253179.

## Summary

Razor is essentially an extremely simple yet powerful way to reduce power consumption in a processor (and also detect possibly missed timing errors). The way this is achieved is by having extra flip flops at latches that are known to be nearer to the timing threshold (probably via static timing analysis). This "shadow latch" has a delayed clock that gets data latched into it after a certain delay, allowing the signal to stabilize for longer. This value is checked against the other latches to check whether the correct value was latched. If the correct value was not, the shadow latch value is used (exclusing when there are metastable states), and this only results in a one cycle penalty as only the stage in front needs to be re-computed. The authors implemented this in a 5 stage in order pipeline and found very impressive results. The power savings varied by benchmark, but there were signficant (up to 40%) power savings. They also showed that this model performs optimally when there are a few critical instructions that fail, and the majority of instructions continue to operate correctly, as the recovery time in most cases is not prohibitive.

## Strengths

- This is the coolest paper I have read so far. I think it is such a simple solution that has so much impact. It's also one of the few papers I have seen where I can see it being very applicable and actually used in industry.

- Having a tapeout to validate the results is also very impressive.

- I think this was also a very well written paper, every sentence was easy to read and follow. It conveyed the information very well.

## Weaknesses

- I would have liked a discussion on why such a simple processor was used, and perhaps a discussion on how this would scale to more complex processors.

## Questions

- I think it is, but is this relevant for OOO machines? They only evaluated on in order processors. Is that a valid comparision (error recovery?)   
    - I say this because I imagine error recovery is not as straight forward for OOO Machines that have structures like the scoreboard, etc.

- "Austin suggested that the DIVA checker could be overdesigned to validate computation from an overclocked core processor"
    - Has there been further work on this that exists? I would like to read more about this.