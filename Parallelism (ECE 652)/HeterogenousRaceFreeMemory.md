# Heterogeneous-race-free memory models
Derek R. Hower, Blake A. Hechtman, Bradford M. Beckmann, Benedict R. Gaster, Mark D. Hill, Steven K. Reinhardt, and David A. Wood. 2014. 
In Proceedings of the 19th international conference on Architectural support for programming languages and operating systems (ASPLOS '14). Association for Computing Machinery, New York, NY, USA, 427–440. https://doi.org/10.1145/2541940.2541981

## Summary

- most CPUs now adopt SC. Not very well understood for heterogenous systems (ie GPUs with a hierarchy of scopes). This paper tries to create a model for scoped synchronization.

- SC for HRF models define correctness in terms of a sequen-
tially consistent execution and rules for what is considered
“enough” synchronization to avoid races.

- The SC for HRF
models achieve two fundamental goals: they provide a pre-
cise definition of memory behavior in a heterogeneous exe-
cution and they provide a framework to describe that behav-
ior in a way that typical programmers can understand. While
we focus on GPUs in this paper due to their prevalence, we
expect the SC-for-HRF concepts and insights to apply to
other heterogeneous parts (e.g., DSPs).

- HRF-direct is release data to shared scope on synchronization
    - may not scale well with modern workloads with irregular parallelism

- In the forward-looking HRF-indirect model, two threads
can synchronize indirectly through a third party even if the
two threads interact with that third party using different
scopes. For example, threads A and C can communicate if A
synchronizes with another thread B using scope S1 and then
B synchronizes with C using scope S2. This type of transi-
tive interaction can enable more irregular parallelism in fu-
ture heterogeneous applications (e.g., in an algorithm in
which A does not know who C is or where C is located).


- at time of writing parallel programming paradigms offer very weak consistency models or none at all. Everything in hand of the programmers.

- In GPUs some synchronization operations are more costly than others (due to scope of synchronization).

## Strengths

## Weaknesses

## Questions

- Fig2. what does memory_order_seq_cst do?


