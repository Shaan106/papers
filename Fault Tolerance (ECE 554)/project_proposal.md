
# Introduction

This project would be a continuation of what I have been building with Prof Hilton. The high level idea is that previous works, such as DIVA, have shown how dynamic verification works and can be used. However, they have not dealt with multicore OOO architectures which come with their own plethora of problems. Previous works (Leveraging 3D Technology for Improved Reliability) have shown that multicore architectures can be verified in this way, and that 3D die stacking is particularly useful for this. However, they trust that load instructions are executed correctly by the OOO core.

# Quick Project Summary

Current state of project is essentially that everything but the memory verification system is working properly, built using gem5. This means, that models of execution verification, register verification, decoding etc are working. The memory verification unit can currently send and receive messages from a custom made banked cache with special porting (to LLC, to checker core, to OOO core). The latencies are modelled well, but the contents of cache, and how the coherence model is affected etc are not yet verified or implemented properly.

The goal of this project is to implement the verification of loads and stores in the architecture discussed with Prof Hilton earlier in the semester. This will be done by splitting store commits and completes, and ensuring that fence instructions are never committed in an order that splits store commits and completes (fence occurred with outstanding stores). Similar things will be done for loads and RMW instructions.

The goal is to try show that this is possible, and hopefully in a realistic way (no crazy unlimited resources approximations). With this it will be possible to 1) detect consistency violations 2) detect load instruction errors in OOO chip that are not covered by ECC 3) (I have not fully thought this part through yet) detect possible coherence model violations, ie if two cores both accidentally access something in M state at the same time.