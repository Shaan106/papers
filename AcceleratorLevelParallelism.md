# Accelerator-level Parallelism

## Paper

Accelerator-level Parallelism \
Mark D. Hill, Vijay Janapa Reddi \
2 July 2019 \
https://arxiv.org/abs/1907.02064

## Abstract

*Future applications demand more performance, but technology advances have been faltering. A promising approach to further improve computer system performance under energy constraints is to employ hardware accelerators. Already today, mobile systems concurrently employ multiple accelerators in what we call accelerator-level parallelism (ALP). To spread the benefits of ALP more broadly, we charge computer scientists to develop the science needed to best achieve the performance and cost goals of ALP hardware and software.*

## Notes

With the death of Moore's Law and Dennard Scaling, how do we continue to deliver performance: **accelerators**

> **accelerators**: hardware components that execute a targeted computa- tion class faster and usually with much less energy.

> We assert there is as yet no “science” for debating and systematically answering basic questions for how to best facilitate broad, flexible, and effective use of multiple accelerators

Above Bit level parallelism, ILP, TLP (thread), DLP (data) there is supposedly ALP. Concurrently apply multiple accelerators for some task.

A lot of accelerators today are locally optimised, however a collection of them used together then is not necessarily globally optimised. Therefore, a better system is needed.

> **_from a compute perspective, we lack the fundamental science on how we must select, size, make efficient, and sometimes combine similar accelerators?_**

> From an integration perspective, how do we best communicate data (shared memory or queues) and control (polling, interrupts, other) among accelerators?

^ a lot of similar, good research questions, these are the ones I really liked.