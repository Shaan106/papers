# Distill: Domain-Specific Compilation for Cognitive Models

## Paper

Distill: Domain-Specific Compilation for Cognitive Models \
Jan Vesely, Raghavendra Pradyumna Pothukuchi, Ketaki Joshi, Samyak Gupta, Jonathan D. Cohen, Abhishek Bhattacharjee \
2022 \ 
https://www.cs.yale.edu/homes/abhishek/jvesely-cgo22.pdf

## Abstract
*Computational models of cognition enable a better understanding of the human brain and behavior, psychiatric and neurological illnesses, clinical interventions to treat illnesses, and also offer a path towards human-like artificial intelligence. Cognitive models are also, however, laborious to develop, requiring composition of many types of computational tasks, and suffer from poor performance as they are generally designed using high-level languages like Python. In this work, we present Distill, a domain-specific compilation tool to accelerate cognitive models while continuing to offer cognitive scientists the ability to develop their models in flexible high-level languages. Distill uses domain-specific knowledge to compile Python-based cognitive models into LLVM IR, carefully stripping away features like dynamic typing and memory management that add performance overheads without being necessary for the underlying computation of the models. The net effect is an average of 27 × performance improvement in model execution over state-of-the-art techniques using Pyston and PyPy. Distill also repurposes classical compiler data flow analyses to reveal properties about data flow in cognitive models that are useful to cognitive scientists. Distill is publicly available, integrated in the PsyNeuLink cognitive modeling environment, and is already being used by researchers in the brain sciences.*

## Results

- Distill enables one widely-studied cognitive model to execute in under five seconds, even though it originally failed to complete within twenty-four hours.

1) Distill, a compilation tool that exploits domain-specific knowledge to provide near-native execution speeds for
cognitive models, along with support to offload computa- tions on accelerators. Distill does not require changes to source code and reuses existing LLVM infrastructure.
2) Discovery that user-guided analyses and optimization can be performed by compiler analysis, and incorporation of this idea into Distill.
3) Evaluation of Distill-accelerated models on single and multicore CPUs and GPU.

## Notes

Cognitive models usually slow to develop as these models are computationally intensive and take days to run. A lot of this is to do with Python's dynamic compilation/code - a lot of which is redundant for this task. Distill acts at the compilation level to allow cognitive models to be developed intiuitively as before in Python while giving a massive performance boost.