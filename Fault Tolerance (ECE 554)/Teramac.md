# The Teramac Custom Computer: Extending the Limits with Defect Tolerance
W. Bruce Culbertson, Rick Amerson, Richard J. Carter, Philip Kuekes, Greg Snider
Hewlett-Packard Laboratories
1996

## Summary

The Teramac system is a multi-chip module (MCM) that is designed to be defect tolerant rather than relying on very strong manufacturing yields. This allows this system to be much cheaper to manufacture than traditional methods (they showed that for MCM modules they were able to at least double yields with some defective modules), allowing for more complex designs and also subsequently provides much more performance at the same price point as traditionally made modules.

Teramac works by having a compile time defect map that is made to identify all defective components in the MCM. This defect map essentially uses overlapping sets of tests to identify defective components. For example, a path is tested, then a subset of the path is tested with different components for the rest of the path. With these overlapping sets it is possible to identify which components are defective, to some granularity depending on how many sets and how overlapped they are. Signal generators run deterministic tests on the system, and the expected outputs are known to test for defects.

Having identified the defects, the system can be reconfigured as it is built upon a "custom computer" (FPGA) based system. This makes the design very usable even with a high (upto 10% in some components) defect rate. The authors show the benefit of such a method, especially when designing very complex systems with many layers that consequently would have a very small yield.

## Strengths

- Really cool idea, shows the practical applications of designing with fault tolerance, how it is more performance for same cost point.

- The overlapping sets of tests is a really interesting idea, and I think it is a really clever way to identify defects.

- Using post-manufacture compile time defect tolerance is also really clever and cool to think about.

## Weaknesses

- It wasn't clear to me what Teramac is being used for, is it just a general purpose computer? Is it being used for specific applications? I think this would have been helpful to know.

- This type of system seems to me like it would only work if there is a lot of redundancy in the design, ie a highly parallel design. This seems to have limited applications in for example a CPU where there is not a lot of redundancy in the design. A discussion of applicable domains would have been helpful.

## Questions

- It seems to me that the authors argue that cost of discarding systems without defect tolerance could be higher than just incorporating defect tolerance into the system and thus discarding less during manufacture. 
    - Do modern chip manufacturers do this?
    - I can imagine in parallel systems (ie GPUs) this would be applicable, letting systems work with defects, as otherwise modern designs would simply have too low of a yield.