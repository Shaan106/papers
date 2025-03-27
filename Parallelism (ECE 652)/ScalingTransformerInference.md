# Efficiently Scaling Transformer Inference
Reiner Pope and Sholto Douglas and Aakanksha Chowdhery and Jacob Devlin and James Bradbury and Anselm Levskaya and Jonathan Heek and Kefan Xiao and Shivani Agrawal and Jeff Dean
2022
https://arxiv.org/abs/2211.05102 

## Summary

This paper addresses the challenges of efficient inference for large Transformer models, focusing on low-latency generation and high-throughput processing with long sequence lengths. The authors develop an analytical framework for selecting optimal multi-dimensional partitioning strategies for large language models based on application requirements, alongside low-level optimizations to achieve better performance on TPU v4 hardware. They aim to provide a set of engineering principles for how best to partition a model in order to scale Transformer inference.

The paper identifies three key challenges for Transformer inference: large memory footprints that exceed single-accelerator capacity, limited parallelizability during generation, and quadratic scaling of attention computation with sequence length. To address these challenges, the authors propose several partitioning strategies tailored to different scenarios, including 1D and 2D weight-stationary layouts for low-batch scenarios and weight-gathered layouts for high-batch throughput.

A major contribution is the analytical framework that helps users understand the tradeoffs between different partitioning strategies and select the optimal approach based on model size, batch size, and sequence length. The authors show that the optimal strategy changes dramatically as these parameters vary, requiring different approaches for input processing (prefill) versus token generation (decode).

The paper also demonstrates how multiquery attention (where multiple query heads share a single key/value head) can be efficiently partitioned over batch dimensions to reduce memory requirements, enabling up to 32× longer context lengths compared to standard multi-head attention. Additional optimizations include parallel formulation of attention/feedforward layers, low-level communication optimizations, and int8 weight quantization.

In their experiments on the PaLM 540B model using 64 TPU v4 chips, the authors achieve 29ms per token latency during generation (using int8 quantization) and 76% model FLOPS utilization (MFU) for large-batch processing, while supporting context lengths of 2048 tokens. Their implementation outperforms NVIDIA's FasterTransformer benchmarks across most configurations.

## Strengths

- I found the decoding latency vs cost graph interesting (Figure 1). It's suprising to see an exponential growth in chip-milliseconds per token.

- Their analytical model provides quite good intuition about which partitioning strategy to use when, based on model size, batch size, and sequence length, rather than requiring exhaustive search (which I was suprised to see was the norm before).

- Their PaLM evaluation was quite nice I thought.

## Weaknesses

- The model seems to be quite specific to TPU hardware, I understand it is for google, but would have been cool to see a bit more generalization.

- They use int8 quantization for weights, I think it would have nice to compare with more aggressive quantization techniques (like 4-bit or binary) that might further improve efficiency.

## Questions

- How would their partitioning strategies apply to GPU architectures with different interconnect topologies than TPU's 3D torus?

- Could you automate this to automatically find optimal partitioning for arbitrary model architectures beyond standard Transformer models?

- Also, just in general, to work on accelerators such as TPUs is a strong background in machine learning required generally, or is it mostly computer architects that pick up machine learning later?
