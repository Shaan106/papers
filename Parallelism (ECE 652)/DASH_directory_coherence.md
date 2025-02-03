# The directory-based cache coherence protocol for the DASH multiprocessor

Daniel Lenoski, James Laudon, Kourosh Gharachorloo, Anoop Gupta, and John Hennessy. 
In Proceedings of the 17th annual international symposium on Computer Architecture (ISCA '90). 
Association for Computing Machinery, New York, NY, USA, 148–159. 
https://doi.org/10.1145/325164.325132

## Summary

This paper presents the design of the DASH processor, and specifically hones in on the directory-based cache coherence model that it uses. This coherence protocol is very different to all of the snooping based protocols that were in use at the time, and this paper essentially presents this new protocol, why it is better than snooping (particularly as the number of processors scales up in newer systems), and the challenges that come with implementing such a cache coherence protocol.

The DASH processor is a shared memory multiprocessor, with each processor having its own cache, and the caches are connected to each other via a high bandwidth network. The key innovation in DASH is the distributed directory-based cache coherence protocol, which introduces shared memory with point-to-point messages, rather than the broadcast mechanisms in snooping based protocols. This allows for a more scalable system as new processors are not difficult to add and do not create a large overhead, however, the lack of a single point of serialization does add new issues.

The key innovation of DASH lies in its distributed directory-based coherence protocol, which addresses three fundamental challenges: correctness, performance, and protocol complexity. For correctness, DASH implements release consistency as its memory model and includes mechanisms to prevent deadlocks and handle error conditions. Performance is optimized through techniques such as cache-to-cache transfers, write buffering, and distributed memory access, while protocol complexity is managed through careful partitioning of control responsibilities among system components.

The main issues in the DASH processor were dealing with correctness (ie dealing with order of execution, consistency models since there is no longer one point of serialization), performance (ie how to make the system not have massive latencies with this new directory based coherence model), and control complexity (ie how not to have massive overheads due to control signals in a distributed processor and distributed memory system).

The protocol supports three primary operations: read requests, read-exclusive requests for writes, and writebacks. Each operation is handled through a combination of local bus transactions and inter-node messages, coordinated by the directory controllers. The system implements several additional features to enhance performance, including queue-based synchronization primitives, prefetch operations, and update writes. The authors also discuss scalability considerations, mentioning that while the current bit-vector directory structure works well for the prototype, alternative approaches would be needed for larger systems. The paper also compares DASH to other contemporary approaches like the IEEE Scalable Coherent Interface (SCI) protocol, and acknowledges the challenges in verifying the correctness of such a complex distributed protocol.

## Strengths

- The paper does a good job of introducing the issues that need to be addressed before choosing a solution. For example, the issues about correctness and consistency models was clearly discussed before release consistency was chosen. Also, the tradeoffs for the choice were also very well explained.

- I think the fact that they built the processor later on helps fix the one part of the paper I did not like (the lack of benchmarks). I think this validates their design and idea beyond any other measure.

## Weaknesses

- Lack of performance modelling, a lot of theory of how this model works. Theoretically this is great, I would have liked to see objective benchmarks to sell the advantage of this model over snooping based protocols.

- The paper seems too theoretical without practical applications. As in, there is a lot of discussion of how certain things (ie deadlocks) will be dealt with. However, there don't seem to be results from their models or proofs of this even though it makes sense. It seems like it would be easy to miss a critical detail.

## Questions

- Why were there no benchmarks conducted when making this paper? Were readers simply to believe that what they said was correct and in fact beneficial?