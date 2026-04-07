# Research Scope

## Working Title
Improving Server-Side Transciphering Efficiency in Hybrid-Homomorphic Encryption Systems

## Context
This project builds on prior work that improved the efficiency of hybrid-homomorphic encryption on the client side by reducing the computational and memory burden on resource-constrained devices. [file:1]
That prior work also showed that the main unresolved cost was shifted to the server, where transciphering introduced a high computational and memory burden. [file:1]

## Main Goal
The goal of this project is to investigate how the efficiency of server-side transciphering in hybrid-homomorphic encryption can be improved. [file:1]
The focus is not on general client-side optimization, but on understanding which factors make transciphering expensive and which optimization directions appear most promising in the current research landscape. [file:1]

## Problem Statement
Hybrid-homomorphic encryption can significantly improve client-side efficiency by encrypting large data volumes symmetrically and only transferring the symmetric key in homomorphically encrypted form. [file:1]
However, this shifts a substantial part of the workload to the server, because the server must perform transciphering in order to convert symmetrically encrypted data into a homomorphic format suitable for later encrypted computation. [file:1]
The predecessor project showed that this server-side transciphering step can be extremely expensive in practice, with very high runtime and substantial memory usage. [file:1]

## Scope
This research focuses on server-side transciphering as the central bottleneck in hybrid-homomorphic encryption systems. [file:1]
It investigates the computational, memory-related, and system-level factors that influence transciphering efficiency, including initialization overhead, runtime cost, scheme choice, framework implementation quality, and related optimization approaches discussed in the literature. [file:1]

## In Scope
- Server-side transciphering in HHE systems. [file:1]
- Computational bottlenecks of transciphering. [file:1]
- Memory bottlenecks of transciphering. [file:1]
- Initialization cost versus steady-state transciphering cost. [file:1]
- Effects of homomorphic and symmetric scheme choice on transciphering efficiency. [file:1]
- Framework, library, and implementation effects on practical server-side performance. [file:1]
- Literature on optimization strategies such as batching, parameter selection, parallelization, compiler support, and hardware acceleration when directly relevant to transciphering. [file:1]

## Out of Scope
- General client-side optimization except where needed as context. [file:1]
- Broad HE theory not directly relevant to transciphering efficiency. [file:1]
- Full deployment architecture beyond what is needed to understand transciphering cost. [file:1]
- Original benchmarking or implementation work in the current phase of the project. [cite:8]

## Current Motivation
The predecessor project demonstrated that HHE can strongly improve client-side efficiency compared with pure TFHE-based encryption on constrained devices. [file:1]
At the same time, it showed that the server-side burden remains a major open issue, because transciphering and related HE processing shift substantial cost to the server. [file:1]
This makes server-side transciphering efficiency the natural next research focus. [file:1]

## Intended Contribution
This project aims to produce a structured understanding of the current state of the literature on server-side transciphering efficiency. [cite:8]
It aims to identify the main bottlenecks, distinguish fundamental cryptographic costs from implementation-dependent overhead, and derive promising directions for later practical optimization work. [file:1][cite:8]
