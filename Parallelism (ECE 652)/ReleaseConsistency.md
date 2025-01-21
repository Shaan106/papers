# Memory Consistency and Event Ordering in Scalable Shared-Memory Multiprocessors
Kourosh Gharachorloo, Daniel Lenoski, James Laudon, Phillip Gibbons, Anoop Gupta, and John Hennessy

## Summary


This paper concerns developing a better memory consistency model for multiprocessor architectures. The authors argue the current models are too strict and do not allow for enough parallelism to be exploited--even with weak consistency. This paper introduces Release Consistency (RC) which is essentially an extension to Weak Consistency. It exploits some additional information about memory access ordering that allows for more aggressive implementations of a program in the hardware level without breaking the correctness of the program (though this does heavily rely on the programmer/compiler to ensure a correct program is written).

The general idea here is to make an even weaker consistency model that is still easy to program for and has the correctness of strict models. The paper defines conflicting accesses as two accesses (ie b1 and b2) on different processes if there exists at least one legal interleaving where b1 and b2 are adjacent in execution. Then RC uses synchronization to order and label these conflicting accesses (using instructions like acquire and release, fences of various types are also used to ensure proper synchronization). These few tools ensure correct execution of the program, and since these rules are mostly programmer/compiler enforced, the hardware can be more aggressive in its optimizations. It is almost entirely the responsibility of the programmer/compiler to provide labels for the accesses, and the less conservative the labeling, the higher is the potential for performance benefits. There are some rules to adhere to when labeling, such as ensuring that the labels are properly nested and that the labels are properly ordered. The paper also discusses the implementation of RC in hardware and how it can be implemented in a scalable manner.

## Strengths

- I liked the clear definitions laid out before the argument was made. It was clear to see what the authors were arguing for and more importantly what they were comparing against.

- I thought the model equivalence section was great and grounded their arguments. It was easy to see the difference between the models once they were made equivalent and then you can infer the differences.

- Diagrams were helpful when present, such as the overlap of hash buckets (which clarified model a bit).

## Weaknesses

- There seemed to be a lot of "there is additional performance here" without many objective metrics. It was easy to see how this might lead to more performance but some real world numbers would have been helpful for the argument.

## Questions

Based on "It is the responsibility of the compiler or the programmer to provide labels for the accesses"
- would you have to check all possible interleavings to find the competing accesses?
- is this not prohibitively expensive, especially for larger more branch heavy programs?

- how are competing accesses practically found (ie temporal location)? Would long latency instructions (ie possible cache miss) not skew during runtime and make it difficult to predict when two accesses will conflict? Actually nvm this is logical compete of accesses.
