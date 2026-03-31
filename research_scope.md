# Research Scope

## Working Title
Server-Side Bottlenecks and Optimization Landscape in Homomorphic and Hybrid-Homomorphic Encryption Systems

## Context
This project builds on previous work that mainly improved client-side efficiency.
My focus is the server side, especially computational bottlenecks, tradeoffs, and open research directions.

## Main Goal
Understand the current state of the landscape for server-side computation in HE/HHE systems.
Identify the main bottlenecks, the most relevant design tradeoffs, and the most promising research directions.

## Research Questions
1. What are the main server-side bottlenecks in HE/HHE systems?
2. Which bottlenecks stem from cryptographic design, and which stem from implementation or system-level choices?
3. In which scenarios is HHE still worthwhile despite shifting workload to the server?

## In Scope
- Server-side transciphering
- Bootstrapping-related cost
- Scheme choice (e.g. TFHE, CKKS, BGV)
- Memory and runtime overhead
- Serialization / data movement overhead
- Framework / library implementation quality
- Literature review of existing approaches and tradeoffs

## Out of Scope
- My own implementation benchmarks for now
- Full production deployment design
- Client-side optimization except where needed for comparison
- Deep mathematical derivations unless directly relevant to bottlenecks

## Key Terms
- HE:
- HHE:
- Transciphering:
- Bootstrapping:
- Ciphertext expansion:
- Server-side throughput:
- Peak memory:

## Current Hypothesis
At the moment, I suspect that transciphering is one of the central server-side bottlenecks in HHE, but I still need to determine how much of that is fundamental and how much depends on implementation quality.

## What Would Count as Progress
- I can explain the main bottleneck categories clearly.
- I can compare at least 3–5 relevant approaches or viewpoints.
- I can identify clear open questions for a thesis or later implementation phase.

## Open Questions
- 
- 
- 

## Last Updated
Date:
