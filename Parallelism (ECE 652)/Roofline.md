# Roofline: an insightful visual performance model for multicore architectures.
Samuel Williams, Andrew Waterman, and David Patterson. 
Commun. ACM 52, 4 (April 2009), 65–76. 
https://doi.org/10.1145/1498765.1498785

# Summary

The roofline model is a model for multicore architectures that aims to provide a general non-specific, easy to compute, and insightful model about how to optimize your multicore system. The case for such a model is that multicore systems have not yet been standardized like traditional single-core systems have been, and so it is hard to know what to optimize for. The roofline model provides a way to visualize the performance of your system and see where you are bottlenecked.

The model is based on the operational intensity of a kernel, which is defined as the number of operations per byte of DRAM traffic. This is a measure of how much computation you can do for a given amount of memory traffic. The model then gives an upper bound on the performance of your system, which is the minimum of the peak floating-point performance and the peak memory bandwidth times the operational intensity. This gives you an idea of how much performance you can expect from your system given the memory bandwidth and the computational power of your system.

The authors provide a few case studies based on the ideas behind 7 dwarves benchmarks. They make benchmarks with varying operational intensities, and then show how the roofline model can be used to optimize these benchmarks for various, very different multicore systems from different vendors. They show how they can use the roofline model here to figure out what they need to optimize and how they might go about implementing these optimizations (ie should they focus on memory bandwidth or computational power, and if so which type of improvement will provide the best effort vs gain tradeoff).

# Strengths

- I find it very interesting that this model exposes usability (lower ridge point better, generally easier to work with, big caveat with IBM having an immature compiler). I suppose I have never really seen an objective benchmark that can give insight into usability, this field seems quite interesting.

- Very good case study, their real-world examples convey their point well. 

- For the purpose of the model (a coarse-grained model to give a general idea of where to optimize) I think this is a very good model. It is simple to compute and gives a surprisingly good idea of where to optimize.

# Weaknesses

- I know they briefly address it in their problems section, but I'm not quite convinced by their argument that a doubled cache size will not lead to a doubled operational intensity. I felt as if in their specific benchmarks it just happened to be that their working set was small enough that the cache size didn't matter, but I can imagine in a more general case this would not be true. Especially when you take multiple processes running on the same core vying for space.

- On a similar note, as far as I understand core to core networks are quite common in multicore systems. This seems to not be touched on. I would like to see how core to core traffic that avoids DRAM but still causes network overhead would affect this model and system.

# Questions

"One reason is the irregular accesses to memory, which you might expect from sparse matrices. The operational intensity varies from 0.17 before a register blocking optimization to 0.25 Flops per byte afterwards."

- This got me thinking - I can imagine sometimes you do a store that is identical to the value you loaded ie a = a * 0. Is this what is happening here? If not, would you gain a lot here, especially in programs like sparse matrix multiplication? I can see how the compiler might do this but what about a = a * b where b is 0?
