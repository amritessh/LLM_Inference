Batching:

Many operations have fixed costs, regardless of data size.

Single prediction overhead vs Batched predictions.

Batch Size Trade-offs
Small Batches (1-32):

Pros: Low latency, low memory usage, good for interactive applications
Cons: Poor hardware utilization, high overhead per sample
Use cases: Real-time inference, online serving

Medium Batches (32-256):

Pros: Balance between latency and throughput
Cons: May not fully utilize large GPUs
Use cases: Most production inference scenarios

Large Batches (256+):

Pros: Maximum throughput, excellent hardware utilization
Cons: High latency, high memory requirements
Use cases: Batch processing, offline inference


2. Caching: Exploiting Data Locality
Cache Hit/Miss Fundamentals
Cache Hit: Data is found in fast memory (cache)

Cost: 1-3 CPU cycles
What happens: CPU gets data immediately from cache
Performance: Optimal speed

Cache Miss: Data not in cache, must fetch from slower memory

Cost: 200-600 CPU cycles (100-200x slower!)
What happens: CPU waits while data is fetched from RAM
Performance: Significant slowdown

Cache Hit Rate: Percentage of memory accesses served from cache


3. Vectorization: Parallel Processing Power
SIMD (Single Instruction, Multiple Data)
Concept: One instruction operates on multiple data elements simultaneously


CPU Optimization

Parallelization strategies: Data Parallelism - Split data across cores. 

Task Parallelism - Different cores do different tasks

CPU Affinity and Pinning - Blinding specific threads/processes to specific CPU cores. 

Cache locality: Keep thread's data in the same core's cache. 

Reduce context switching: Avoid expensive core migrations.

NUMA Optimization - Keep threads close to their memory. 

Branch prediction Optimization

GPU optimization, Mastering parallel computing:

CUDA: Execution Hierarchy, Thread Indexing

Global Memory, Shared Memory

Memory access optimization, coalesced access pattern, bank conflicts in shared memory. 

Hardware Profiling, CPU Performance Metrics. 

GPU Performance Metrics 

Memory bandwidth analysis: 
Theoretical vs Achieved bandwidth

Memory Access Pattern analysis

Integrated Profiling Workflow
Performance Debugging Process: 

System-Level Monitoring

Optimization Decision Tree: 
Step1: Identify Primary Bottleneck 
Step2: Apply Targeted optimization 

Advanced CPU Optimization Techniques 
NUMA(Non uniform memory access optimization)



CPU Governor and Frequency Scaling

Thread Pool Optimization.

GPU Optimization unleashing parallel power. 

Multi GPU Coordination. 


