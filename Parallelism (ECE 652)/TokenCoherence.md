

# Token coherence: decoupling performance and correctness

Milo M. K. Martin, Mark D. Hill, and David A. Wood. 2003.  
In Proceedings of the 30th annual international symposium on Computer architecture (ISCA '03). 
Association for Computing Machinery, New York, NY, USA, 182–193. https://doi.org/10.1145/859618.859640

## Summary

- optimize for the common case and so don't introduce extra overheads.
- correct the uncommon case with extra substrate

The paper introduces Token Coherence, a protocol to allow low-latency cache-to-cache misses without requiring ordered interconnects. The key innovation is separating coherence into two parts: a correctness substrate that ensures safety by tracking tokens, and a performance protocol that optimizes common cases. The correctness substrate maintains a fixed number of tokens per memory block and enforces rules where processors need at least one token to read data and all tokens to write data.

The paper gives a specific example in TokenB, a performance protocol that broadcasts requests directly to processors without going through ordering points. When races occur, TokenB reissues requests until successful, falling back to persistent requests if needed. This approach achieves the low latency of snooping protocols while working on unordered interconnects like torus networks, which traditional snooping cannot use because of ordering requirements.

Their benchmarks show that TokenB significantly outperforms both snooping and directory protocols. The protocol is faster than snooping because of the lower-latency unordered interconnects, and faster than directory protocols by avoiding indirection through the home node for cache-to-cache misses. However, TokenB uses moderately more bandwidth than directory protocols but the additional traffic is manageable in systems with modern links.

## Strengths

- I really like this idea. It originates from the simple idea of optimizing for the common case yet it provides up 20% better perfomance (which seems like a lot).

- I appreciated the clear benchmarks and comparision, and also the tradeoffs in extra bandwidth needed for this.

- Good formal definitions of invariants, that was nice to disambiguate the protocol.

## Weaknesses

- Perhaps some more discussion on the tradeoffs would be nice. It's easy to get more performance with more things, but how would this affect cache overheads, complexity and especially power consumption.

## Questions

- I was curious about how the protocol would perform in systems with more complex memory hierarchies (ie non-uniform).
