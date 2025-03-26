# An In-Network Architecture for Accelerating Shared-Memory Multiprocessor Collectives

Benjamin Klenk, Nan Jiang, Greg Thorson, and Larry Dennison. 
In Proceedings of the ACM/IEEE 47th Annual International Symposium on Computer Architecture (ISCA '20). 
IEEE Press, 996–1009. https://doi.org/10.1109/ISCA45697.2020.00085

## Summary

This paper presents a novel architecture for accelerating collective communication operations, particularly All-Reduce, in shared-memory multiprocessor systems with a focus on GPU-based deep learning workloads. The authors identify All-Reduce as a critical bottleneck in distributed deep learning training, showing it can consume up to 30-42% of training time in state-of-the-art systems. To address this bottleneck, they propose hardware extensions to the network fabric that enable in-network computation of collective operations.

The paper introduces two complementary methods for in-network reductions: a "pull" method where GPUs issue multicast load requests that gather and reduce data from multiple sources, and a "push" method where GPUs write data to the network which is then reduced at designated aggregation points. These approaches are designed specifically for shared-memory systems with millions of concurrent threads, unlike previous approaches that focused on message-passing CPU-centric models requiring complex reservation protocols.

The authors implement both methods using reduction tables in network switches that can perform arithmetic operations on data in-flight. They also propose a wave synchronization mechanism to regulate network traffic and prevent congestion. Their design is evaluated through detailed simulations of systems ranging from 16 to 128 GPUs, showing performance improvements of up to 2x for large messages and 18x for small messages compared to state-of-the-art software algorithms, translating to up to 1.4x faster deep learning training for networks like Transformer.

The main innovation is the architecture's ability to work within the constraints of shared-memory GPU systems, where packets represent individual memory operations rather than larger messages, and where the execution order of millions of threads can be arbitrary and non-deterministic. The paper also discusses practical implementation considerations including switch architecture requirements, deadlock avoidance, error handling, and DMA engine extensions to efficiently use the proposed reduction methods.

## Strengths

- Very clear problem and clear, thorough analysis followed by evaluation. No real ambiguity left.

- I liked the two complementary designs (pull and push methods) with different trade-offs in implementation complexity and performance.

## Weaknesses

- They estimated the area overhead of their design to be less than 1% of a switch chip, but there's no analysis of power consumption or other hardware costs that might affect whether this design is truly feasible or not.

- The simulation-based evaluation doesn't really compare with other hardware acceleration techniques for this. Are there other approaches to even compare against?

- I generally found the paper to be a bit too wordy - I felt like a lot of their points could be significantly condensed without losing much information.

## Questions

- I'm curious about what the SHArP system is that they mention in the related work. How does it differ from what they are doing?

- The methods produce non-deterministic results for floating-point operations - are floating point operations just always hard and researchers just ignore the problems associated with them? Is floating point being non-deterministic ok? I can imagine this would make reproducability (especially in ML) very difficult.