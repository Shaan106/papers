# Improving Direct-Mapped Cache Performance by the Addition of a Small Fully-Associative Cache and Prefetch Buffers

## Paper
Improving Direct-Mapped Cache Performance by the Addition of a Small Fully-Associative Cache and Prefetch Buffers \
Norman P. Jouppi \
The 17th Annual International Symposium on Computer Architecture (ISCA), pp. 364-373 \
June 1990 \
https://users.cs.duke.edu/~lkw34/papers/jouppi-victimcache-isca1990.pdf

## Problem Description and Motivation

The paper addresses the performance limitations caused by cache misses in direct-mapped caches, which are used for their fast access times but suffer from conflict misses due to their lack of associativity. Cache misses, especially in future high-performance processors, can severely impact overall system performance. With projections of processors reaching peak performance of 1,000 MIPS, cache design improvements are crucial to prevent memory hierarchy bottlenecks that could cause significant performance losses.

## Main Ideas/Approach

The paper proposes three hardware techniques to reduce cache misses:

1. **Miss Caching**: A small fully-associative cache is added between the direct-mapped first-level cache and the second-level cache. This cache holds 2-5 entries and is checked on every miss. If the requested data is found in this miss cache, it reduces the miss penalty to a single cycle.

2. **Victim Caching**: An enhancement of miss caching, this technique stores the victim (the data that was evicted) in the small fully-associative cache rather than the requested data. Victim caches (1-5 entries) are highly effective at reducing conflict misses, where multiple data lines map to the same cache location.

3. **Stream Buffers**: Prefetch buffers that fetch and store subsequent cache lines after a miss. This reduces capacity and compulsory misses, as well as some conflict misses. The prefetched data is stored in a buffer, not in the cache itself, to avoid cache pollution.

The combined use of victim caches and stream buffers reduces the miss rate by 2-3x in large benchmark tests.

## Strengths and Weaknesses

### Strengths
- **Practicality**: The proposed techniques (miss caches, victim caches, and stream buffers) are simple and inexpensive in terms of hardware and implementation. They offer substantial performance improvements with a small amount of additional hardware.
- **Comprehensive Coverage**: The paper thoroughly evaluates multiple methods to address both conflict and capacity misses, showing significant performance gains across a range of benchmarks.

### Weaknesses
- **Limited Scalability Discussion**: While the paper focuses on first-level caches, there is limited analysis on the impact of these techniques on second-level caches or larger cache sizes. The scalability to multi-level cache hierarchies could have been explored further.
- **Benchmark Scope**: The benchmarks used do not include workloads like multiprogramming or operating system tasks, which might exhibit different behavior and potentially affect the observed performance improvements.

## Questions for Discussion

1. How would Victim Caches work with cache coherence?
2. Can we use these methods to second-level caches?