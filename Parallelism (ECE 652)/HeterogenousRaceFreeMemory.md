# Heterogeneous-race-free memory models
Derek R. Hower, Blake A. Hechtman, Bradford M. Beckmann, Benedict R. Gaster, Mark D. Hill, Steven K. Reinhardt, and David A. Wood. 2014. 
In Proceedings of the 19th international conference on Architectural support for programming languages and operating systems (ASPLOS '14). Association for Computing Machinery, New York, NY, USA, 427–440. https://doi.org/10.1145/2541940.2541981

## Summary

Most CPUs now adopt SC. The idea of consistency is not very well understood for heterogenous systems (ie GPUs with a hierarchy of scopes). This paper tries to create a model for scoped synchronization. They introduce the idea of sequential consistency for heterogeneous systems called SC for HRF (heterogeneous race free). They propose two models: HRF-direct and HRF-indirect. The first model is more restrictive, but the second model allows for more flexibility in synchronization by using intermediary threads to synchronize across scopes.

The idea behind the paper in one line is "implementing sequential consistency in heterogenous systems by enforcing scoped synchronization". Their model is evaluated via gem5 on benchmarks to show the speedup using this programming paradigm. They also argue that (especially HRF-indirect) is flexible and easily to understand for the programmer.

## Strengths

- Suprisingly simple idea that is extremely powerful. I think it introduces simple rules that benefit heterogenous systems a lot.

- The visualizations and diagrams (especially the code examples) were very helpful in giving concrete cases of where these ideas were powerful.

## Weaknesses

- Very little evaluation, and on a very small subset of programs. I like the idea, but I think more validation of the performance is necessary.

- I also felt as if things were made much more complicated than they needed to be. Simpler wording would have been nicer.

## Questions

- Fig2. what does memory_order_seq_cst do?

- I felt as if there could have been more evaluation and benchmarking, but thinking more about it, it seems hard to do with such a contribution. How would you evaluate this? Have a lot of code generated for different benchmarks using this model and then compare?


