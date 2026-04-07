# Research Scope

## Working Title
Improving Server-Side Transciphering Efficiency in Hybrid-Homomorphic Encryption Systems

## Context
This project builds on prior work that improved the efficiency of hybrid-homomorphic encryption on the client side by reducing the computational and memory burden on resource-constrained devices. 
That prior work also showed that the main unresolved cost was shifted to the server, where transciphering introduced a high computational and memory burden. 

## Main Goal
The goal of this project is to investigate how the efficiency of server-side transciphering in hybrid-homomorphic encryption can be improved. 
The focus is not on general client-side optimization, but on understanding which factors make transciphering expensive and which optimization directions appear most promising in the current research landscape. 

## Problem Statement
Hybrid-homomorphic encryption can significantly improve client-side efficiency by encrypting large data volumes symmetrically and only transferring the symmetric key in homomorphically encrypted form. 
However, this shifts a substantial part of the workload to the server, because the server must perform transciphering in order to convert symmetrically encrypted data into a homomorphic format suitable for later encrypted computation. 
The predecessor project showed that this server-side transciphering step can be extremely expensive in practice, with very high runtime and substantial memory usage. 

## Scope
This research focuses on server-side transciphering as the central bottleneck in hybrid-homomorphic encryption systems. 
It investigates the computational, memory-related, and system-level factors that influence transciphering efficiency, including initialization overhead, runtime cost, scheme choice, framework implementation quality, and related optimization approaches discussed in the literature. 

## In Scope
- Server-side transciphering in HHE systems. 
- Computational bottlenecks of transciphering. 
- Memory bottlenecks of transciphering. 
- Initialization cost versus steady-state transciphering cost. 
- Effects of homomorphic and symmetric scheme choice on transciphering efficiency. 
- Framework, library, and implementation effects on practical server-side performance. 
- Literature on optimization strategies such as batching, parameter selection, parallelization, compiler support, and hardware acceleration when directly relevant to transciphering. 

## Out of Scope
- General client-side optimization except where needed as context. 
- Broad HE theory not directly relevant to transciphering efficiency. 
- Full deployment architecture beyond what is needed to understand transciphering cost. 
- Original benchmarking or implementation work in the current phase of the project. 

## Current Motivation
The predecessor project demonstrated that HHE can strongly improve client-side efficiency compared with pure TFHE-based encryption on constrained devices. 
At the same time, it showed that the server-side burden remains a major open issue, because transciphering and related HE processing shift substantial cost to the server. 
This makes server-side transciphering efficiency the natural next research focus. 

## Intended Contribution
This project aims to produce a structured understanding of the current state of the literature on server-side transciphering efficiency.
It aims to identify the main bottlenecks, distinguish fundamental cryptographic costs from implementation-dependent overhead, and derive promising directions for later practical optimization work. 

## Research Questions

### Primary Research Question
How can the efficiency of server-side transciphering in hybrid-homomorphic encryption systems be improved?

### Secondary Research Questions
1. What are the dominant computational and memory bottlenecks in server-side transciphering?
2. Which part of the observed transciphering cost is inherent to the cryptographic design, and which part results from framework, library, or implementation choices? 
3. How important is initialization overhead compared with the cost of the transciphering process itself? 
4. How do the chosen homomorphic and symmetric schemes affect transciphering efficiency and practicality? 
5. Which optimization directions appear most promising in the current literature, such as parameter tuning, batching, parallelization, compiler support, or hardware acceleration?
6. Under which conditions does HHE remain worthwhile when the client-side gains are accompanied by substantial server-side transciphering cost? 

## Working Hypothesis
Server-side transciphering is a major practical bottleneck in HHE systems because the client-side efficiency gains of HHE are partly offset by the high runtime and memory burden introduced on the server.
A substantial part of this burden may be reduced through better system design, implementation quality, and newer optimization approaches, but part of the cost may also be intrinsic to the cryptographic structure of transciphering itself.
