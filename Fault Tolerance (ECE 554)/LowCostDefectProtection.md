# Ultra low-cost defect protection for microprocessor pipelines.
Smitha Shyam, Kypros Constantinides, Sujay Phadke, Valeria Bertacco, and Todd Austin. 
SIGOPS Oper. Syst. Rev. 40, 5 (December 2006).
https://doi.org/10.1145/1168917.1168868

## Summary

The idea behind BulletProof is to dynamically protect processors from silicon defects. They introduce an approach that provides high coverage of silicon defects (89%) with little area cost (5.8%). They also claim that without defect there is little to no performance impact, and with defects slowdown is only 4-18%. The idea is to use on-line distributed built-in self-testing techniques to verify the functional integrity of the hardware. This is done by exploiting idle cycles to test the hardware. The authors claim that this approach is more efficient than traditional redundancy techniques. Each stage (ie decode, ALU, memory checking, cache etc) is checked with unique minimal hardware, so that they can optimize for area.

### Strengths

- "We do not graph the performance impacts directly because there simply were none!"
    - This is really cool, I have a question about its realism though.

- Idea of slowing down clock to keep hardware alive is neat (although I think this is pretty common/not novel?)

### Weaknesses

- The usage of VLIW processors generalized to all processors was kind of sketchy.
    - Paper assumes there is inbuilt redundancy in the systems that is easy to exploit (ie just do redundancy checks for decoders)

- Does not deal with design time faults at all, although could work well in conjunction with other techniques.

## Questions

- Can the lack of performance degradation be attributed to a bad compiler? As in the compiler is simply letting too many bubbles into the VLIW system?

- What if you are testing all the components (let's say for simplicity Decode then ALU then Memory) and after you have tested Decode, a transient fault occurs in Decode but the code block is committed and no later faults are found so it is thought to be ok? This seems to have been missed.
    - I later read the part about not dealing with transients, but then how would you integrate a transient check system into this?