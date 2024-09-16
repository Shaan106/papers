# Computers, Complexity, and Controversy

## Paper

Computers, Complexity, and Controversy \
Robert P. Colwell, Charles Y. Hitchcock m, E. Douglas Jensen, H. M. Brinkley Sprunt, and Charles P. Kollar \
IEEE Computer, vol. 18, no. 9, pp. 8–19 \
September 1985

## Problem Description and Motivation

This paper attempts to identify and provide guidance on how to better conduct computer architecture research concerning comparision and evaluation of RISC and CISC systems. The main motivation is that the authors believe that the current methods of comparing RISC and CISC systems are flawed and that the results are not reliable. Specifically, they believe that RISC is often overly glorified by research, often beyond its true capabilities, and that CISC research does not produce enough standardised results to allow for true comparison between the two architectures.

## Main Ideas/Approach

The paper looks at the debate between RISC and CISC architectures, emphasizing that the focus should not be on just the complexity and size of instruction sets. The authors instead argue that the research between CISC and RISC architectures should be more than just statistics from benchmarks, especially as these benchmarks are often very limited in their scope and real-world applicability (such as the use of the fibonnaci sequence and not considering things like the operating system).

The paper points out that the RISC architecture is not strictly defined, and the definition is often loosely thrown around. And so, the authors start off by defining what they believe makes a RISC architecture in a strict manner, and show how oftentimes people claim to have created RISC processors which are not nearly in line with what a RISC processor should truly be. 

One of the main points put forward by the paper is that RISC and CISC are not black and white approaches, yet research and the wider media seems to portray the architectures like that. Instead the authors urge the idea that this is a spectrum, and instead of pledgining allegiance to one architecture, architects should use a mix of ideas from both that best achieve their overall processor performance goals.

The authors also argue that some of the advantages attributed to RISC, such as the large performance gains from overlapping register sets, are not exclusive to RISC designs and can be applied to CISC architectures as well. And, that often times in real world situations, the heavily research based RISC processor falls short (such as the MCF evaluation), showing that the real-world applications are often missed in research based studies. They also criticize the oversimplification of performance claims for RISC architectures, mentioning that other factors such as compiler efficiency, memory management, and application environment, play significant parts in overall system performance.

## Strengths and Weaknesses

### Strengths
I think that the paper does a very good job in highlighting the issues in RISC research being done. It highlights it very effectively, and further provides methods in which these problems can be removed. Furthermore, it helps provide an alternative perspective that many, like myself, hadn't considered - that there is a middle ground between RISC and CISC that may be better, and that not considering that is a big mistake.

### Weaknesses
The paper makes good argumenets, however I feel as if it is biased. The paper provides a lot of valid arguments about why RISC design is not as good as claimed, and that researchers don't often evaluate their designs in a way that would be relevant for real-world applications. However, the paper provides little to no arguments against CISC,instead treating it as almost a better ISA. I think that there could have been more done to show the flaws within the CISC architecture, and how in some cases RISC does have an advantage, giving a better balanced argument.

## Questions for Discussion
I feel as if CISC architectures were built up as the field of computer architecture was built up. Backwards compatibility and the existence of previous generations of hardware design essentially leant itself to the development of CISC designs. If possible, would chips today be significantly better if we could essentially have a "clean slate" and design a new ISA from the ground up to implement all of our chips in? Are we limited at all by artifacts from previous generations of chips (in lets say for example x86 designs)?