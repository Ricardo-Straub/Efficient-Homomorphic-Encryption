# Decision Log

---

## Entry

### Date
2026-04-27

### Topic
Promising optimization directions and implementation choices for CKKS-based transciphering

### What I Currently Believe
- The current literature suggests that CKKS transciphering throughput can be improved substantially through techniques such as CKKS/CI-CKKS context conversion, BB-BTS, lazy SubByte evaluation, and free-XOR style optimizations for XOR-heavy Boolean circuits.
- These reported gains appear strongest in settings with large SIMD-style batch sizes, AES-CTR-style workloads, and hardware/software environments close to the ones used by the authors, especially GPU-backed execution in the “Less than 1ms” paper.
- For my likely setup, especially smaller batch sizes and no dedicated GPU, the practical gains may be smaller than the headline numbers reported in the papers.
- XBOOT looks especially relevant for XOR-heavy CKKS transciphering because it reduces the depth cost of XOR handling and reports strong improvements for AES-style workloads.
- Lattigo currently looks like the more realistic implementation starting point for my work because it is open source and is explicitly used in XBOOT, whereas access to the authors’ HEaaN-based implementation is uncertain.
  
### Why I Believe It
- Authors reported achieving 0.994ms per AES block for 215215 AES-128 blocks, 1.58× faster throughput than XBOOT in the same implementation environment, and can process 2929 blocks in 2.67s on one GPU.
- Authors reported reduceing AES-CKKS round depth from 9 to 3, lowers the modulus size from 1555 bits to 830 bits, reduces the ring degree from 216216 to 215215, and achieves AES transciphering of 256 KB in 236 seconds with 5× lower latency and 2.5× higher throughput than the prior state of the art.
-  The open-source HEAAN/HEaaN family exists publicly in older or related forms, but the specific implementation used in recent high-throughput CKKS transciphering work is not something I can currently assume access to.

### Main Supporting Sources
- High-Throughput AES Transciphering using CKKS: Less than 1ms
- XBOOT: Free-XOR Gates for CKKS with Applications to Transciphering
- 

### What Could Change My Mind
- I get access to the authors’ implementation from High-Throughput AES Transciphering using CKKS: Less than 1ms and it works well in my environment.
- A benchmark on my actual target setup shows that the reported advantages do not translate well to smaller batch sizes or CPU-only/macOS execution.
- Another library or implementation path turns out to be easier to build, test, and modify than Lattigo while still supporting the CKKS features I need.

### What I Am Not Confident About
- Whether I will get access to the authors’ HEaaN-based implementation.
- How much of the reported throughput gain depends specifically on GPU support and very large batch sizes.
- Whether Lattigo is only the most accessible starting point or also the best long-term choice for my project

### Practical Consequence
- Prioritize an implementation path that is reproducible and accessible now, which currently points toward Lattigo, while separately trying to obtain HEaaN access for comparison.

### Next Action
- Email the authors of High-Throughput AES Transciphering using CKKS: Less than 1ms to ask whether their implementation is available for research use.
- Try and get access to HEanN

---

## Entry

### Date
2026-04-21

### Topic
Polynomial discrete-CKKS integer arithmetic: latency vs throughput and domain-switching

### What I Currently Believe
- This paper suggests that a fully polynomial discrete-CKKS framework can achieve lower latency than recent CKKS-based integer-arithmetic approaches for additions, multiplications, comparisons, and logical shifts, at least in the reported experiments.
- The main tradeoff is worse throughput, because the representation and SIMD layout consume many slots, especially for multiplication.
- A major conceptual contribution is domain-switching: the same CKKS parameter set can support approximate real computation and later integer-style computation, without relying on modular reduction via functional bootstrapping.


### Why I Believe It
- The paper explicitly claims lower latency than the current state of the art across additions, multiplications, comparisons, and logical shifts, while noting lower throughput due to representation choices.
- The paper argues that unlike recent functional-bootstrapping-heavy approaches, its method can use a more standard CKKS parameterization with roughly 15 multiplicative levels before bootstrapping, enabling switching between R-CKKS and Z-CKKS under the same parameter set.

### Main Supporting Sources
- A flexible and polynomial framework for integer arithmetic in CKKS 
- 
- 

### What Could Change My Mind
- If later work shows that the latency advantage disappears once throughput, total work, or end-to-end application performance is considered rather than single-operation timings.
- If the claimed flexibility from domain-switching turns out to be less practically useful than the paper suggests in real workloads.
- 

### What I Am Not Confident About
- Whether lower latency but lower throughput is a good tradeoff for workloads with many values or for large-scale server-side processing.
- How relevant this is for our project, since our bottleneck is server-side transciphering in HHE rather than generic encrypted integer arithmetic in CKKS. 
- Whether the domain-switching idea is genuinely useful in our pipeline or mainly interesting for other application classes

### Practical Consequence
- Discrete-CKKS landscape is becoming more flexible, not just faster.

### Next Action
- Clarify: Do we use approximate or exact-style encrypted computation?
- Clarify: Lower latency worth the lower throughput?

---

## Entry

### Date
2026-04-21

### Topic
What has changed in the HHE landscape in 2026?

### What I Currently Believe
- Large lookup tables in CKKS functional bootstrapping seem significantly more practical than in earlier work.
- The CMT-FBT approach looks especially promising for larger LUT sizes.
- However, I am not yet convinced that these gains transfer directly to our HHE/transciphering setting, especially under limited server resources.

### Why I Believe It
- The paper proposes two new algorithms intended to reduce runtime and memory complexity for large LUT evaluation in CKKS functional bootstrapping.
- The authors report that CMT-FBT achieves the best amortized runtime for larger LUT sizes in their benchmarks.
- Their OpenFHE proof-of-concept shows strong speedups, including a reported 47.5x gain for a 16-bit LUT, and evaluates LUTs up to 24 bits.- 
- 

### Main Supporting Sources
- Evaluating Larger Lookup Tables using CKKS 
- 
- 

### What Could Change My Mind
- If later reading shows that the reported gains come mainly from engineering optimizations such as lazy rescaling, parallelization, or implementation tuning rather than from the core collapsed-tree / multiplexer-tree idea.
- If follow-up work shows that memory use or hardware requirements make the method impractical outside large-server settings.
- If the method is not relevant for exact HHE/transciphering workloads.- 
- 

### What I Am Not Confident About
- Whether this paper is directly relevant to our project, since our main bottleneck is server-side transciphering in HHE rather than general CKKS LUT evaluation.
- Whether approximate CKKS-based LUT evaluation is useful for our use case at all.
- How much of the reported improvement is algorithmic versus implementation-specific.- 
- 

### Practical Consequence
- I should treat this paper as a signal that the broader HE landscape is evolving, especially around functional bootstrapping and LUT evaluation.
- But I should not yet let it shift the thesis focus away from TFHE/transciphering unless I find a concrete connection to our problem.

### Next Action
- Read:
- Compare:
- Clarify: whether any of the ideas are transferable to exact transciphering or server-side HHE optimization.
- Postpone:

---

## Entry

### Date
YYYY-MM-DD

### Topic

### What I Currently Believe

### Why I Believe It
- 
- 
- 

### Main Supporting Sources
- 
- 
- 

### What Could Change My Mind
- 
- 
- 

### What I Am Not Confident About
- 
- 
- 

### Practical Consequence

### Next Action
- Read:
- Compare:
- Clarify:
- Postpone:
