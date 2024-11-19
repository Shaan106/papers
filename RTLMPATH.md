

## Paper  
**RTL2MµPATH: Multi-µPATH Synthesis with Applications to Hardware Security Verification**  
Yao Hsiao, Nikos Nikoleris, Artem Khyzha, Dominic P. Mulligan, Gustavo Petri, Christopher W. Fletcher, Caroline Trippel  
*Published in Hardware Security Verification Proceedings.*


## Problem Description and Motivation  
The paper identifies limitations in existing tools like RTL2µSPEC that synthesize abstract hardware models (µSPEC) for formal verification. Specifically, RTL2µSPEC assumes that each instruction follows a single microarchitectural execution path (µPATH). This assumption is invalid for modern processor designs with features like caches, speculative execution, and variable latency units, which create multiple µPATHs per instruction. This limitation restricts the verification of hardware security vulnerabilities, such as side-channel leaks.

To address these challenges, the authors propose RTL2MµPATH, a tool that discovers all possible µPATHs for an instruction and extends it with SYNTHLC to detect and formally verify hardware side-channel vulnerabilities.


## Main Ideas/Approach  

1. **Multi-µPATH Synthesis**:  
   - **RTL2MµPATH** analyzes SystemVerilog designs to automatically synthesize all µPATHs for instructions, overcoming the single-µPATH limitation.  
   - The approach incorporates cycle-accurate modeling and micro-op finite state machines (µFSMs) to capture granular execution details.  

2. **Security Implications**:  
   - µPATH variability is a strong indicator of hardware side channels. A side channel exists when operand-dependent µPATH differences can leak private data to attackers.  
   - Transponders and Transmitters: Transponders exhibit µPATH variability, while transmitters cause operand-dependent modulations of shared resources.  

3. **SYNTHLC for Leakage Verification**:  
   - Extends RTL2MµPATH with symbolic information flow analysis to generate leakage contracts, a formal description of side-channel vulnerabilities.  
   - Leakage contracts support defenses like constant-time programming and speculative execution mitigation strategies.  

4. **Case Studies**:  
   - Demonstrated on the RISC-V CVA6 core and its cache subsystem. Discovered 94 unique leakage signatures and 26 transmitters.  
   - Identified a novel channel involving store and load address operands.

## Strengths and Weaknesses  

### Strengths  
- **Generalized Approach**: Handles µPATH variability, supporting complex processor features like speculation and caches.  
- **Comprehensive Security Verification**: Enables detection of both known and novel side channels using leakage signatures.  
- **Scalability**: Modular synthesis approach supports realistic, large-scale processor designs.  

### Weaknesses  
- **Metadata Dependency**: Requires detailed annotations like µFSMs and operand mappings, which might not always be readily available.  
- **Verification Overhead**: High complexity of symbolic analysis can lead to performance bottlenecks during synthesis.  
- **Precision Limitations**: May generate false positives or miss nuanced side-channel behaviors under specific conditions.

## Questions for Discussion  
1. Are there additional processor features or hardware structures (e.g., GPU pipelines) where this methodology could be extended?  