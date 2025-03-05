# SWIFT: software implemented fault tolerance

G. A. Reis, J. Chang, N. Vachharajani, R. Rangan and D. I. August,
International Symposium on Code Generation and Optimization, 
San Jose, CA, USA, 2005, pp. 243-254, 
doi: 10.1109/CGO.2005.34.

## Summary

This paper presents a software based technique to detect transient faults in single-threaded processors. The idea is that the compiler creates redundancy in the machine code by inserting redundant instructions as well as check instructions. This idea builds heavily off of previous research (EDDI), extending it significantly. Specifically, the control flow checking mechanisms are improved and certain aspects (such as memory checking) are loosened and delegated to ECC. The authors then optimize this EDDI+ECC+CFE for speed leading to SWIFT. SWIFT is then shown on benchmarks being compared to EDDI+ECC+CFE and NOFT, being generally much faster and on par with the best at fault detection.

## Strengths

- Really cool idea, easy to see their new contributions.

- I especially liked how they provided metrics for several modes of comparison (binary size, IPC, fault detection rate etc).

- I like how a clear invariant is established
    "As long as we can ensure that stores execute only if they are “meant to” and stores write the correct data to the correct address, the system will run correctly."

## Weaknesses

- Multicore is hard, ensuring order is difficult. However, most modern stuff works with multicore so would be cool to see something on this in future.

- There are a few performance optimizations made here (ie omitting comparisons of signatures) for performance, but this significantly increases fault-time recovery time (ie would be harder to recover from there). This would have been nice to comment on more, even if fault recovery isn't really done.

## Questions

"These results are in accordance with previous research [27, 9] which observed that many faults injected into programs do not result in incorrect output."
    - evaluation, inserted many random faults. They say many of these don't lead to incorrect operation. Interesting? Should you not evaluate more objectively with a coverage of critical faults?

- Did this kind of control flow checking inspire argus?