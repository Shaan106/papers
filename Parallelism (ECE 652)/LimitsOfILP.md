# Limits of Instruction-Level Parallelism
David W. Wall

## Summary

This paper is written at a time where parallelism is starting to get utilized to further processor performance, yet a lot of the area around parallelism is unexplored. The general aim of the paper seems to be to give some rough guidelines to the state of instruction level parallelism today - how much "exists" and how much is being exploited (and how).

Specifically, this paper builds upon previous works addressing their shortcomings. Previous papers had at the time delved deep into exploiting the parallelism in blocks (that is the parallelism that exists between easily contiguously executable instructions, such as between branches). This paper argues that there is a lot more parallelism that can be exploited if inter-block parallelism is considered.

The paper creates many idealized models of computation to show how much parallelism is exploited in each case. The parameters considered are mainly type and capability of alias analysis, number of registers and scheme for register renaming, and the accuracy and capability of the branch and jump predictors. Then these somewhat idealized models are tested on benchmarks and the "parallelism" extracted by each model is plot and discussed.

Overall the paper argues that there is still a lot more ILP to be exploited, but this parallelism is clearly more available and unexploited in certain categories. The paper especially stresses the amount of parallelism available through inter-block parallelism, and so stresses the importance of very good branch predictors (hardware or software) in order to exploit this potential performance gain.

## Strengths

- The visualizations and explanations do a good job in backing up the arguements being made with the data being presented.

- The paper provides a good overview of where future work should be guided for parallelism, how it actually lies in speculative execution for larger effective contexts.

- I liked how clear the introduction and conclusion were, and how I knew what the arguement being made was from the start, and letting the rest of the paper back up that arguement.

- This paper does a good job in addressing the shortcomings of its own methods. The conclusion very clearly states a lot of considerations that I thought were not being accounted for in the paper. Especially things such as not accounting for long latency instructions (cache miss etc), and modelling everything very idealistically.

## Weaknesses

- A lot of the design choices for the simulator feel ambiguous and not backed by anything concrete. I think it would have been helpful to have models such as "fair" or "good" be related to real world equivalents or to perhaps back the parameter choices with some stronger data or arguments. It is not completely clear to me why that particular set of parameters was chosen for a "fair" model.

- It would have been nice to have some tradeoffs at least discussed. For example, a lot of the paper is about if we increase this number we get more throughput, but what are the hardware costs of that? For example, would you have to slow down the clock with more hardware? Would the die area be a problem? Would there be significantly more routing logic that could result in more ILP but at the same time possibly less throughput?

- I did not quite get why those particular benchmarks were chosen to be tested upon, although this could be because I'm not too familiar with these benchmarks.

## Questions

- I would assume a lot of parallelism is down to how a program is written. How much of this parallelism is down to the compiler and how much is down to the programmer? Can a compiler almost always extract the maximum parallelism from a program?

- This work provides a very idealized view of where parallelism lies and is yet to be exploited. How are studies like this interpreted and actually used in the real world? 

