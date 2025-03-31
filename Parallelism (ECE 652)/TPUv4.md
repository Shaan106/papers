# TPU v4: An Optically Reconfigurable Supercomputer for Machine Learning with Hardware Support for Embeddings
Norm Jouppi, George Kurian, Sheng Li, Peter Ma, Rahul Nagarajan, Lifeng Nai, Nishant Patil, Suvinay Subramanian, Andy Swing, Brian Towles, Clifford Young, Xiang Zhou, Zongwei Zhou, and David A Patterson. 
2023. 
In Proceedings of the 50th Annual International Symposium on Computer Architecture (ISCA '23). 
Association for Computing Machinery, New York, NY, USA, Article 82, 1–14. https://doi.org/10.1145/3579371.3589350

## Summary

This paper talks about the TPU v4 which has been deployed since 2020. The main problem they are addressing is to do with the fact that Google relies a lot on machine learning models, and the training of these models is computationally, monetarily and energetically expensive. Furthermore, with the advent of larger and larger models (ie LLMs), the training of these models is becoming an even harder task (I liked how they said that this was a very much a "happily for architects" kind of thing).

This scale also raises a lot of reliability issues that google can't deal with via simple redundancy like they do with their google search services. For training, everything must work in the way defined, whereas in a search no-one can really tell if a few results are missing. They had three main ways of addressing their problems:

They addressed reliability and scale by introducing Optical Circuit Switches (OCSes) with optical data links, allowing a 4K-node supercomputer through reconfiguration to tolerate 1K CPU hosts that are unavailable 0.1%–1.0% of the time. They also disclosed the hardware support for embeddings in DLRMs (which suprisingly are a very important task for them). Then they leveraged the first two capabilities to enable flexible topologies, including twisted torus, which has better bisection properties which significantly improved the performance of the system.

The TPU v4 system uses a 4x4 cube as a basic building block, with optical connections between blocks. This allows for completely reconfigurable topologies, which means that they no longer need to block out a static size of TPUs, and can be more general and therefore have higher utilization. Furthermore, the lookup operations are mostly bottlenecked by the memory bandwidth, memory capacity, and VPU (vector processing unit) performance. This means that more FLOPS are not necessarily the answer to better performance, but rather densely encoding data so that models train better on them. The end-to-end embedding lookup performance is essentially proportional to the bisection bandwidth due to the all-to-all transfers of small embedding vectors.

## Strengths

- Firstly, this is really cool and I did not know just quite the extent of how much better the TPU in raw numbers is compared to other hardware like the A100.

- I really liked the fact that this was a "in hindsight" paper, where the authors were not only able to sell their ideas but the real life applications of them. This is a great way to show the impact of the work although I realise that this is not possible for the majority of academic papers.

## Weaknesses

- I found some of the figures such as figure 12 very confusing. Was this trying to show that workloads get faster with more nodes? What was the purpose here?

- I thought the architecture vs technology could have been seperated and evaluated a bit better. It would have been nice to see how much of a gain each part of the architecture was responsible for. It felt a bit like "this did a lot" without many numbers behind.

## Questions

- How much of a role does the software for the TPU play? I imagine something like CUDA would need to be developed to run programs on the TPU. Is this hard to do? Is this software much less mature than Nvidia's?

- I didn't really understand the Goodput metric - what does this represent?

- "About 40% of the performance/Watt improvement was from technology and the rest was from design improvements (e.g., balancing the pipeline, implementing clock gating)."
    - how was this measured?
