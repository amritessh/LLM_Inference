Latency vs Throughput:

Latency(Response Time)

Definition: Time from sending a request to receiving the complete response.

Throughput (Processing Rate)
Definition: Number of requests processed per unit time
Units: Requests per second (RPS), queries per second (QPS)
What it measures: "How many requests can I handle simultaneously?"

Optimization Strategies
For Low Latency:

Smaller batch sizes (even batch size = 1)
Model quantization and pruning
Edge deployment (closer to users)
Dedicated hardware per request

For High Throughput:

Large batch sizes
Request queuing and batching
GPU utilization optimization
Parallel processing across multiple devices

CPU Cache Hierarchy (Fastest → Slowest)
L1 Cache (Level 1):

Size: 32-64 KB per core
Latency: ~1 CPU cycle (0.3-1 ns)
Purpose: Store most frequently accessed data
Analogy: Items on your desk you use constantly

L2 Cache (Level 2):

Size: 256 KB - 1 MB per core
Latency: ~3-10 CPU cycles (1-3 ns)
Purpose: Recently accessed data that doesn't fit in L1
Analogy: Items in your desk drawer

L3 Cache (Level 3):

Size: 8-32 MB shared across cores
Latency: ~10-40 CPU cycles (3-12 ns)
Purpose: Shared cache for all CPU cores
Analogy: Bookshelf in your office


How These Concepts Connect in ML Systems
Memory Bandwidth as the Bottleneck
Why GPU Memory Bandwidth Matters:
Modern ML models are often memory-bound, not compute-bound:
Example: Large Language Model Inference
- Model: 70B parameters × 2 bytes = 140 GB weights
- GPU memory bandwidth: 2000 GB/s
- Time to read all weights once: 140/2000 = 0.07 seconds
- But we need to read weights multiple times per inference!
Cache Optimization in Practice
Good Cache Usage:
python# Process data in blocks that fit in cache
block_size = 1024  # Fits in L3 cache
for i in range(0, data_size, block_size):
    process_block(data[i:i+block_size])
Poor Cache Usage:
python# Random access destroys cache performance
for i in random.shuffle(range(data_size)):
    process_element(data[i])
Latency vs Throughput in Real Systems
Interactive Chatbot (Latency-Critical):
Goal: <200ms response time
Strategy: 
- Batch size = 1 (immediate processing)
- Model on GPU with high-speed memory
- Optimized for single-request speed
Result: Great user experience, expensive per request
Batch Text Processing (Throughput-Critical):
Goal: Process 1M documents/hour
Strategy:
- Large batch sizes (256-1024)
- Queue requests and process in groups
- Optimize GPU utilization over response time
Result: Cost-efficient, higher overall capacity

:For ML specifically, the most critical takeaway is that inference performance is often memory-bound rather than compute-bound, meaning how efficiently you move data matters more than raw computational power.
