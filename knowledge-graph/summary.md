# AI Infra 学习摘要

- 更新时间：2026-08-05T16:26:40+08:00
- 概念数：35
- 教学事件数：37
- 关系边数：123

## 掌握度总览

| 概念 | 掌握度 | 需复习 | 下次复习 | 别名 |
|---|---:|:---:|---|---|
| All-to-All | L1 | 否 | 2026-07-27 | 全交换, All2All |
| AllGather | L1 | 否 | 2026-07-27 | 全收集 |
| AllReduce | L1 | 否 | 2026-07-27 | 全规约 |
| BF16 | L1 | 否 | 2026-08-03 | bfloat16, Brain Floating Point 16 |
| CPU-GPU Communication | L1 | 否 | 2026-08-04 | CPU–GPU通信, Host-Device Data Movement |
| CUDA | L1 | 否 | 2026-07-28 | Compute Unified Device Architecture, CUDA Programming Model, GPU Memory Hierarchy |
| CUDA Streams | L1 | 否 | 2026-08-04 | CUDA Stream and Event, CUDA流与事件 |
| Compute-Communication Overlap | L1 | 否 | 2026-07-27 | 计算通信重叠, overlap, 隐藏延迟 |
| Context Parallelism | L1 | 否 | 2026-07-30 | CP, 上下文并行 |
| D2H | L1 | 否 | 2026-08-04 | Device-to-Host, GPU到CPU传输 |
| DDP | L1 | 否 | 2026-07-27 | DistributedDataParallel, 分布式数据并行 |
| Distributed Training Communication | L1 | 否 | 2026-07-27 | 大模型训练通信方式, 集合通信, Collective Communication |
| Expert Parallel | L1 | 否 | 2026-07-27 | EP, 专家并行 |
| FP16 | L1 | 否 | 2026-08-03 | Half Precision |
| FP8 Training | L1 | 否 | 2026-08-03 | FP8混合精度训练, E4M3/E5M2 Training |
| FSDP | L1 | 否 | 2026-07-27 | Fully Sharded Data Parallel, 完全分片数据并行, ZeRO-3 |
| GPUDirect | L1 | 否 | 2026-08-04 | GPUDirect RDMA, GPUDirect Storage |
| H2D | L1 | 否 | 2026-08-04 | Host-to-Device, CPU到GPU传输 |
| Low-Bit Quantization | L1 | 否 | 2026-08-03 | 低比特量化, INT8/INT4 Quantization |
| Megatron | L1 | 否 | 2026-07-28 | Megatron-LM, Megatron Core |
| Mixed Precision Training | L1 | 否 | 2026-08-03 | 混合精度训练, AMP |
| Mixture of Experts | L1 | 否 | 2026-07-30 | MoE, Sparse Mixture of Experts, 混合专家 |
| Multi-Dimensional Parallelism | L1 | 否 | 2026-07-30 | 3D Parallelism, 4D Parallelism, 5D Parallelism, 多维并行 |
| NCCL | L1 | 否 | 2026-07-28 |  |
| NUMA | L1 | 否 | 2026-08-04 | Non-Uniform Memory Access |
| Numerical Precision | L1 | 否 | 2026-08-03 | 数值精度, 大模型精度 |
| OpenAI Triton | L1 | 否 | 2026-07-28 | Triton, triton-lang |
| Pinned Memory | L1 | 否 | 2026-08-04 | Page-Locked Memory, 锁页内存 |
| Pipeline Parallel | L1 | 否 | 2026-07-27 | PP, 流水线并行 |
| PyTorch | L1 | 否 | 2026-07-28 | torch |
| ReduceScatter | L1 | 否 | 2026-07-27 | 规约散射 |
| Tensor Parallel | L1 | 否 | 2026-07-27 | TP, 张量并行 |
| Unified Memory | L1 | 否 | 2026-08-04 | CUDA Managed Memory, 统一内存 |
| Virtual Pipeline Parallelism | L1 | 否 | 2026-07-28 | VPP, 虚拟流水线并行, Interleaved Pipeline Parallelism |
| torch.compile | L1 | 否 | 2026-07-28 |  |

## 关系

- FSDP --prerequisite--> Compute-Communication Overlap
- FSDP --contrasts--> DDP
- FSDP --contrasts--> Tensor Parallel
- FSDP --contrasts--> Pipeline Parallel
- FSDP --implements--> AllGather
- FSDP --implements--> ReduceScatter
- Distributed Training Communication --prerequisite--> Compute-Communication Overlap
- Distributed Training Communication --related--> FSDP
- Distributed Training Communication --component--> AllReduce
- Distributed Training Communication --component--> AllGather
- Distributed Training Communication --component--> ReduceScatter
- Distributed Training Communication --component--> All-to-All
- Distributed Training Communication --related--> Tensor Parallel
- Distributed Training Communication --related--> Pipeline Parallel
- AllReduce --component--> Distributed Training Communication
- AllReduce --enables--> DDP
- AllReduce --related--> ReduceScatter
- AllReduce --related--> AllGather
- AllGather --component--> Distributed Training Communication
- AllGather --enables--> FSDP
- AllGather --contrasts--> ReduceScatter
- ReduceScatter --component--> Distributed Training Communication
- ReduceScatter --enables--> FSDP
- ReduceScatter --related--> AllReduce
- All-to-All --component--> Distributed Training Communication
- All-to-All --enables--> Expert Parallel
- DDP --implements--> AllReduce
- DDP --contrasts--> FSDP
- DDP --related--> Distributed Training Communication
- Tensor Parallel --implements--> AllReduce
- Tensor Parallel --implements--> AllGather
- Tensor Parallel --contrasts--> FSDP
- Tensor Parallel --related--> Distributed Training Communication
- Pipeline Parallel --related--> Distributed Training Communication
- Pipeline Parallel --contrasts--> FSDP
- Expert Parallel --implements--> All-to-All
- Expert Parallel --related--> FSDP
- Expert Parallel --related--> Distributed Training Communication
- Virtual Pipeline Parallelism --implements--> Pipeline Parallel
- Virtual Pipeline Parallelism --related--> Compute-Communication Overlap
- CUDA --enables--> PyTorch
- CUDA --enables--> OpenAI Triton
- CUDA --component--> NCCL
- PyTorch --implements--> CUDA
- PyTorch --enables--> OpenAI Triton
- PyTorch --related--> Megatron
- OpenAI Triton --implements--> CUDA
- OpenAI Triton --related--> PyTorch
- OpenAI Triton --component--> torch.compile
- Megatron --related--> PyTorch
- Megatron --related--> Pipeline Parallel
- Megatron --related--> Virtual Pipeline Parallelism
- Megatron --related--> Tensor Parallel
- CUDA --enables--> Compute-Communication Overlap
- Virtual Pipeline Parallelism --prerequisite--> Pipeline Parallel
- Virtual Pipeline Parallelism --implements--> Megatron
- Mixture of Experts --enables--> Expert Parallel
- Mixture of Experts --implements--> All-to-All
- Mixture of Experts --related--> Megatron
- Mixture of Experts --related--> PyTorch
- Context Parallelism --contrasts--> Tensor Parallel
- Context Parallelism --related--> Pipeline Parallel
- Context Parallelism --component--> Multi-Dimensional Parallelism
- Multi-Dimensional Parallelism --component--> DDP
- Multi-Dimensional Parallelism --component--> FSDP
- Multi-Dimensional Parallelism --component--> Tensor Parallel
- Multi-Dimensional Parallelism --component--> Pipeline Parallel
- Multi-Dimensional Parallelism --component--> Virtual Pipeline Parallelism
- Multi-Dimensional Parallelism --component--> Context Parallelism
- Multi-Dimensional Parallelism --component--> Expert Parallel
- Numerical Precision --component--> Mixed Precision Training
- Numerical Precision --component--> BF16
- Numerical Precision --component--> FP16
- Numerical Precision --component--> FP8 Training
- Numerical Precision --component--> Low-Bit Quantization
- Numerical Precision --related--> CUDA
- Numerical Precision --related--> PyTorch
- Mixed Precision Training --related--> Numerical Precision
- Mixed Precision Training --related--> PyTorch
- Mixed Precision Training --related--> CUDA
- BF16 --related--> Numerical Precision
- BF16 --contrasts--> FP16
- FP16 --related--> Numerical Precision
- FP16 --contrasts--> BF16
- FP16 --related--> Mixed Precision Training
- FP8 Training --related--> Numerical Precision
- FP8 Training --implements--> Mixed Precision Training
- FP8 Training --related--> CUDA
- Low-Bit Quantization --related--> Numerical Precision
- Low-Bit Quantization --related--> PyTorch
- CPU-GPU Communication --component--> H2D
- CPU-GPU Communication --component--> D2H
- CPU-GPU Communication --related--> Pinned Memory
- CPU-GPU Communication --related--> CUDA Streams
- CPU-GPU Communication --related--> NUMA
- CPU-GPU Communication --contrasts--> Unified Memory
- CPU-GPU Communication --related--> GPUDirect
- CPU-GPU Communication --related--> CUDA
- CPU-GPU Communication --related--> Compute-Communication Overlap
- H2D --related--> CPU-GPU Communication
- H2D --related--> Pinned Memory
- H2D --related--> CUDA Streams
- D2H --related--> CPU-GPU Communication
- D2H --related--> Pinned Memory
- D2H --related--> CUDA Streams
- Pinned Memory --enables--> H2D
- Pinned Memory --enables--> D2H
- Pinned Memory --related--> CPU-GPU Communication
- CUDA Streams --related--> CUDA
- CUDA Streams --enables--> Compute-Communication Overlap
- CUDA Streams --related--> H2D
- CUDA Streams --related--> D2H
- NUMA --related--> CPU-GPU Communication
- NUMA --related--> Pinned Memory
- Unified Memory --contrasts--> CPU-GPU Communication
- Unified Memory --related--> H2D
- Unified Memory --related--> D2H
- GPUDirect --related--> CPU-GPU Communication
- GPUDirect --related--> D2H
- GPUDirect --related--> H2D
- Mixture of Experts --component--> Expert Parallel
- Mixture of Experts --component--> All-to-All
- Mixture of Experts --enables--> Compute-Communication Overlap

## 概念详情（每个点包含输出过的信息）

### All-to-All  (掌握度 L1)
- 别名：全交换, All2All

**一句话结论**
All-to-All（全交换）：每张卡都持有要发给所有其他卡的不同数据块；通信后每张卡收到来自所有其他卡发给自己的块。本质是跨卡的“矩阵转置式重分布”。

**关键图：数据流**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**机制与用途**
用在哪：MoE 的 Expert Parallel。不同专家分布在不同卡上，每个 token 经 router 后要被发往它选中的专家所在的卡——这是一次 All-to-All(dispatch)；专家算完再 All-to-All 送回(combine)。每个 MoE 层两次 All-to-All。

**能否 overlap**
能但更难。依赖 router 输出（先知道每个 token 去哪），依赖链较紧。先进实现（DeepSeek DualPipe、Tutel）会把 dispatch 的 All-to-All 与其他专家的计算或 dense 部分计算重叠，工程复杂度显著高于 AllReduce overlap。

**常见误区**
把 All-to-All 当廉价操作：MoE 跨机 All-to-All 常是训练瓶颈，且专家负载不均会让部分链路拥塞。走 IB 时尤其敏感。
- 关联：component→Distributed Training Communication; enables→Expert Parallel

### AllGather  (掌握度 L1)
- 别名：全收集

**一句话结论**
AllGather（全收集）：每张卡持有一个分片，通信后每张卡都拿到拼接起来的完整数据。只搬运不做规约，是 ReduceScatter 的逆操作。

**关键图：数据流**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**机制与用途**
用在哪：
• FSDP/ZeRO-3：前向/反向前用 AllGather 把分片的参数临时拼回完整层参数，算完释放。
• Tensor Parallel：列并行线性层各卡算出输出的一部分，用 AllGather 拼成完整激活给下一层。
• 序列并行：在“序列切分”和“张量切分”之间转换时用到。

**公式与量级**

```
每卡通信量 ≈ (N-1)/N × M_full ≈ M_full   （N 较大时）
  M_full = 拼接后完整数据的字节数
对 FSDP：一层参数越大，这次 AllGather 越贵，所以要靠 prefetch 与计算重叠。
```

**能否 overlap**
能。FSDP 用 forward_prefetch/backward_prefetch：算第 i 层时提前 AllGather 第 i+1 层参数，把通信藏进计算里。

**常见误区**
误把 AllGather 当作带求和的操作：它只做数据搬运/拼接，不做任何规约。带求和的是 AllReduce/ReduceScatter。
- 关联：component→Distributed Training Communication; enables→FSDP; contrasts→ReduceScatter

### AllReduce  (掌握度 L1)
- 别名：全规约

**一句话结论**
AllReduce（全规约）：每张卡各持一份等长数据（通常是梯度），逐元素求和（或求平均）后，结果每张卡都得到一份完整的和。它是数据并行的命脉。

**关键图：数据流**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**机制**
N 张卡各自在不同 mini-batch 上算出本地梯度 g_i，反向结束后对梯度做 AllReduce，让每张卡都拿到全局和 G = Σ g_i（除以 N 即全局平均梯度），从而各自更新出完全一致的参数。

高效实现是 Ring AllReduce：分成 reduce-scatter 阶段（沿环累加）+ all-gather 阶段（沿环传播结果），把带宽利用率做到接近最优。

**公式与量级**

```
Ring AllReduce 每卡通信量：
  ≈ 2 × (N-1)/N × M ≈ 2M   （N 较大时）

  M = 待规约数据总字节数（如梯度总大小）
  N = 参与卡数

关键：通信量几乎与卡数 N 无关（趋近 2M），这是能 scale 到数千卡的原因。
例：7B 模型 fp16 梯度 M=14GB，每卡 AllReduce ≈ 28GB。
```

**最小 Sample**

```
import torch, torch.distributed as dist
# 每张卡持有本地梯度 grad（shape 相同）
dist.all_reduce(grad, op=dist.ReduceOp.SUM)   # 原地求和，每卡都得到 G
grad /= dist.get_world_size()                 # 变成全局平均梯度
# DDP 内部对每个 bucket 自动做上面这件事，并与反向计算重叠
```

**能否 overlap**
能，且是训练优化头等大事。反向逐层从后往前算，第 L 层梯度一算完就能立刻 AllReduce，同时继续算前面层。PyTorch DDP 用 gradient bucketing 自动实现：梯度攒满一个 bucket 就异步触发 AllReduce。

**常见误区**
1) 误以为通信量随卡数线性增长：错，Ring 每卡趋近 2M，几乎与 N 无关。
2) 把 AllReduce 当成 FSDP 的省显存手段：AllReduce 后每卡都拿完整梯度仍冗余，FSDP 才用 ReduceScatter 把它降到 1/N。
- 关联：component→Distributed Training Communication; enables→DDP; related→ReduceScatter; related→AllGather

### BF16  (掌握度 L1)
- 别名：bfloat16, Brain Floating Point 16

**格式**

```
1 sign + 8 exponent + 7 mantissa；2Byte；最大值约3.39e38；1附近间隔约0.0078125。
```

**为什么适合LLM**
动态范围接近FP32，不易发生FP16式大范围溢出或小梯度下溢，通常无需Loss Scaling。

**代价**
尾数少，小更新和局部差异更容易舍入；累加、Norm、Softmax和Optimizer仍常保留FP32。

**与FP16**
BF16范围更大；FP16在1附近更精细。二者同为2Byte。

**适用**
现代Ampere及以后GPU的大模型预训练、微调与Serving基线。
- 关联：related→Numerical Precision; contrasts→FP16

### CPU-GPU Communication  (掌握度 L1)
- 别名：CPU–GPU通信, Host-Device Data Movement

**一句话结论**
CPU适合控制、分支、IO和小任务；GPU适合大规模规则并行。H2D/D2H是两套内存之间的数据搬运，优化顺序是少传、合并、Pinned、异步、Overlap和拓扑绑定。

**CPU-GPU数据路径**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**CPU与GPU对比**
CPU强调低延迟、复杂控制和系统IO；GPU强调吞吐、SIMT、Tensor Core与HBM。GPU是否值得取决于计算收益能否覆盖H2D+D2H+Launch+Sync。

**Pageable与Pinned**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**双缓冲Overlap**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**256MiB算例**

```
[B=8,S=4096,H=4096] BF16为256MiB；有效H2D带宽24GB/s时约11.18ms。若计算8ms，串行19.18ms，理想流水稳态11.18ms，吞吐约提升1.72倍。
```

**训练流水线**
CPU准备Batch i+2、H2D复制Batch i+1、GPU计算Batch i并行；稳态周期约max(T_cpu_prepare,T_H2D,T_gpu_compute)。

**优化目标**
可改善Latency、Throughput、GPU利用率、CPU占用、PCIe带宽与尾延迟；通常不直接减少GPU常驻显存，除非结合Offload。

**高级路径**
Unified Memory统一寻址但仍可能迁移；Mapped Pinned适合稀疏一次性访问；GPUDirect RDMA/GDS让NIC或Storage直接DMA到GPU。

**失败模式**
大量小拷贝、热路径临时Pin、non_blocking后立即同步、Pinned源提前复用、D2H后CPU过早读取、忽略NUMA和误把Unified Memory当零成本。
- 关联：component→H2D; component→D2H; related→Pinned Memory; related→CUDA Streams; related→NUMA; contrasts→Unified Memory; related→GPUDirect; related→CUDA; related→Compute-Communication Overlap

### CUDA  (掌握度 L1)
- 别名：Compute Unified Device Architecture, CUDA Programming Model, GPU Memory Hierarchy

**一句话结论**
CUDA 执行层级决定谁处理哪份数据：kernel→grid→block→thread，硬件以 32-thread warp 为调度单位，把 block 分配到 SM。内存层级决定数据搬运成本：register/shared 在片上，L2 全 GPU 共享，global memory 通常落在 HBM。性能优化的核心是减少 HBM 往返并提高片上复用，同时控制寄存器/shared 压力。

**线程层级到 SM**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**统一 SAXPY 数值例子**

```
N=2²⁰ float32；block=256；grid=4096；每 block=8 warps。z=a*x+y 每元素读 8 Byte、写 4 Byte、约 2 FLOP。总有用流量=12 MiB，计算量≈2.10 MFLOP，AI≈0.167 FLOP/Byte，典型 memory-bound。
```

**Grid / Block / Thread / Warp**
Thread 是编程语义；block 是协作和资源分配单元，整个 block 驻留在一个 SM，可共享 shared memory 并用 __syncthreads()；grid 是一次 launch 的全部 blocks，普通 kernel 中 block 间默认不能直接同步。warp 固定 32 threads，是硬件调度粒度；同一 warp 走不同分支会产生 divergence。

**内存层级**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**寄存器、Shared 与 HBM**
Register 每线程私有、最快，但用量过高降低 occupancy；spill 后进入逻辑 local memory，物理上通常在设备显存。Shared memory 每 block 共享，适合 tile 复用和数据重排，但要避免 bank conflict。HBM 容量最大、延迟高，依靠 coalescing、cache、片上复用和多 warp 隐藏延迟。

**Coalescing 与 Bank Conflict**

```
一个 warp 32 个线程连续读 float32，请求 128 Byte，常见规则下覆盖 4×32-Byte segments。stride=2 时 128 Byte 有用数据散布在约 256 Byte 范围，理想效率≈50%。Shared 中 tile[32][32] 按列访问可形成 32-way conflict；改为 tile[32][33]，步长 33 mod 32=1，可分散到不同 banks。
```

**Occupancy 与 Roofline**

```
Occupancy=active warps per SM÷maximum warps per SM。active blocks 由 thread、register、shared memory 和架构上限中最紧项决定。AI=FLOP÷Byte；可达到性能≤min(峰值计算吞吐, 可达到内存带宽×AI)。Occupancy 是隐藏延迟的手段，不是最终 KPI。
```

**最小 CUDA Kernel**

```
__global__ void saxpy(float a,const float* x,const float* y,float* z,int n){
  int i=blockIdx.x*blockDim.x+threadIdx.x;
  if(i<n) z[i]=a*x[i]+y[i];
}
// N=1<<20, threads=256, blocks=(N+threads-1)/threads
```

**工程调优路径**
先确保索引/shape 正确，再用 profiler 定位热点；计算算术强度和有效带宽；检查 coalescing、requested/actual throughput；评估 register/shared 复用与压力、bank conflict、spill、warp stall；扫 block/tile 参数；最终回到训练 step 的端到端吞吐。

**常见误区**
Thread 不是硬件调度粒度，warp 才是；local memory 名字含 local 但通常不在片上；shared memory 只有存在复用/重排价值时才值得使用；100% occupancy 不保证最快；两个 stream 也不保证真正 overlap。
- 关联：enables→PyTorch; enables→OpenAI Triton; component→NCCL; enables→Compute-Communication Overlap

### CUDA Streams  (掌握度 L1)
- 别名：CUDA Stream and Event, CUDA流与事件

**核心语义**
同一Stream按提交顺序执行；不同Stream无默认相对顺序，具备并发可能但不保证。

**Overlap时间线**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**Event依赖**

```
with torch.cuda.stream(copy_stream):
    y=x.to('cuda',non_blocking=True)
    done=copy_stream.record_event()
torch.cuda.current_stream().wait_event(done)
```

**wait与record**
wait_stream/wait_event解决执行依赖；Tensor.record_stream解决Caching Allocator的内存生命周期。

**性能边界**
Copy Engine、SM、PCIe、HBM可能共享资源；时间线重叠不等于传输完全被隐藏。

**计时**
异步操作应用CUDA Event计时；普通CPU时钟若不在边界同步，常只测到提交时间。
- 关联：related→CUDA; enables→Compute-Communication Overlap; related→H2D; related→D2H

### Compute-Communication Overlap  (掌握度 L1)
- 别名：计算通信重叠, overlap, 隐藏延迟

**一句话结论**
Overlap 的本质是：让 GPU 在等待某件慢事情（通信、数据搬运、CPU 下发指令）完成时不要闲着，而是同时去做另一件不依赖该结果的事情，从而用并行把等待时间“藏”起来。

它的实现依赖三个底层能力：异步执行 + 多条独立的执行流(stream/engine) + 依赖关系管理。理想情况下总时间 ≈ max(计算, 通信)，而不是二者相加。

**直觉：餐厅上菜模型**
把 GPU 想象成厨师，把通信/拷贝想象成“跑堂端菜到隔壁桌”。

• 没有 overlap（串行）：厨师炒完一道菜 → 亲自端出去 → 回来再炒下一道。端菜时厨师完全空闲。
• 有 overlap：厨师炒完一道菜交给跑堂去端（异步），自己立刻开始炒下一道。端菜和炒菜同时进行。

关键前提：炒下一道菜不依赖“上一道菜已经端到桌上”。如果有依赖就无法重叠。类比失效点：现实中跑堂(通信引擎)和厨师(计算SM)可能抢同一资源(如显存带宽、SM)，所以 overlap 不是完全免费的并行。

**底层逻辑：为什么 GPU 能 overlap**
1) GPU 执行是异步的：CPU 调用 kernel 后不等它执行完，把任务提交到队列就立即返回，GPU 在后台执行。下发与执行解耦，CPU 才有机会提交别的任务。

2) GPU 有多个独立执行引擎：Compute Engine(SM) 执行计算 kernel；Copy Engine(DMA) 专门做显存拷贝(H2D/D2H)，独立于 SM；NCCL 通信通常也是 kernel，占用 SM 或专用路径。Copy Engine 与 Compute Engine 物理独立，所以“拷贝”和“计算”天然可真并行。

3) CUDA Stream：表达“哪些任务可以并行”。同一条 stream 内 FIFO 串行；不同 stream 之间默认无顺序约束，可自由并行。所以 overlap 的实现套路就是：把两件想并行的事放进两条不同 stream，用 event 管理跨流依赖。

**关键图：串行 vs 重叠的时间线**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**公式与量级**

```
无 overlap（串行）:  T_total = T_comp + T_comm
理想 overlap:        T_total ≈ max(T_comp, T_comm)

例：T_comp = 100 ms, T_comm = 40 ms
  串行  = 100 + 40 = 140 ms
  重叠  = max(100, 40) = 100 ms   → 加速 1.4×，省约 28.6%

例：T_comm = 120 ms（通信占比更大）
  串行  = 100 + 120 = 220 ms
  重叠  = max(100, 120) = 120 ms  → 加速 1.83×

物理下界：T_total ≥ max(T_comp, T_comm)，永远不可能更低。
```

**最小 Sample：拷贝-计算 overlap**

```
import torch
N_CHUNKS = 4
copy_stream = torch.cuda.Stream()   # 一条流负责拷贝
comp_stream = torch.cuda.Stream()   # 一条流负责计算

# pinned 内存是 overlap 成立的隐藏前提，否则拷贝退化成同步
host = [torch.randn(1024,1024).pin_memory() for _ in range(N_CHUNKS)]
dev  = [torch.empty(1024,1024, device='cuda') for _ in range(N_CHUNKS)]
out  = [None]*N_CHUNKS

for i in range(N_CHUNKS):
    with torch.cuda.stream(copy_stream):
        dev[i].copy_(host[i], non_blocking=True)   # 异步拷贝第 i 块
    comp_stream.wait_stream(copy_stream)           # 跨流依赖
    with torch.cuda.stream(comp_stream):
        out[i] = dev[i] @ dev[i]                   # 计算第 i 块
torch.cuda.synchronize()

# 效果：算第 i 块时，第 i+1 块的拷贝同时进行
# 要点：overlap = 拆分 + 多流 + 依赖管理
```

**常见误区与失败模式**
1) 误以为多流一定并行：若两条流都要用 SM 而 SM 已被占满，通信 kernel 抢不到资源，overlap 名存实亡（NCCL 占 SM 是典型）。
2) 忘记 pinned memory：拷贝退化成同步，overlap 失效，而且不报错只是变慢，极难发现。
3) 依赖没管好：跨流没用 event 同步，计算读到没传完的数据，导致数值错误或 NaN。
4) bucket 太小：每次通信太小，启动开销占比过高反而变慢；太大又减少重叠机会。
5) 只看平均不看时间线：必须用 Nsight Systems / torch.profiler 确认计算块和通信块真的在时间上重叠。

### Context Parallelism  (掌握度 L1)
- 别名：CP, 上下文并行

**一句话结论**
Context Parallelism沿Sequence维切网络输入和全部Activation，使每Rank只长期保存S/CP个Token；Attention中本地Q仍需完整上下文KV，因此通过Ring P2P或AllGather交换KV，Backward对dKV执行对应ReduceScatter/归约。

**Shape例子**

```
B=2,S=8,H=16,CP=2：全局X[2,8,16]→本地[2,4,16]。TP2且Q Heads=4、KV Heads=2时，每TP Rank本地Q[2,4,2,4]、K/V[2,4,1,4]；CP交换后逻辑可见KV长度8。
```

**Attention通信**
Linear、LayerNorm、MLP不跨Token，可在本地Sequence Chunk运行。Attention的每个Query需要整个序列的Keys/Values；实现可流式Ring交换KV边收边算，避免物化完整KV。Backward归约dK/dV到其Owner Rank。

**显存与性能**

```
Activation Memory理想约降1/CP；本地Token计算约降1/CP。代价是每Attention Layer的KV通信、Causal负载均衡和更小计算Chunk。GQA/MQA减少KV Heads，可显著降低CP通信。
```

**CP与SP区别**
SP通常依附TP，只切LayerNorm/Dropout等非TP区域激活；CP是独立Process Group，切输入和几乎全部激活，并专门处理Attention跨Context依赖。SP通常要求TP>1，CP可在TP=1时使用。

**适用场景**
适合8K+长上下文、Activation OOM、希望减少Full Recomputation或避免继续扩大TP的场景。要求Attention Kernel支持CP/Ring并具备高速互联和正确Sequence整除/打包。
- 关联：contrasts→Tensor Parallel; related→Pipeline Parallel; component→Multi-Dimensional Parallelism

### D2H  (掌握度 L1)
- 别名：Device-to-Host, GPU到CPU传输

**定义**
Device Memory→Host Memory。用于业务结果、Checkpoint、CPU后处理、日志、调试和Offload。

**优化原则**
先在GPU做Reduction、Top-k、Sampling或压缩，只返回CPU真正需要的小结果。

**同步边界**
non_blocking D2H返回不代表CPU结果可读；CPU执行numpy、打印、序列化前必须等待Copy Event/Stream。

**异步模式**

```
cpu_out=torch.empty(y.shape,dtype=y.dtype,pin_memory=True)
cpu_out.copy_(y,non_blocking=True)
done=torch.cuda.current_stream().record_event()
done.synchronize()
consume(cpu_out)
```

**Serving例子**

```
Batch128、Vocab128K的FP16 Logits约32MiB；GPU采样后只返回128个int32约512Byte，Payload减少约65536倍。
```
- 关联：related→CPU-GPU Communication; related→Pinned Memory; related→CUDA Streams

### DDP  (掌握度 L1)
- 别名：DistributedDataParallel, 分布式数据并行

**一句话结论**
DDP（Distributed Data Parallel，分布式数据并行）：每张卡保存一份完整的模型副本，各自吃不同的数据分片，反向后用 AllReduce 同步梯度，使各卡参数保持一致。

**关键图：机制**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**机制**
每 step：各卡在自己的数据分片上前向+反向算出本地梯度 → AllReduce 求全局平均梯度 → 各卡用相同梯度独立更新，参数天然保持一致。PyTorch DDP 用 gradient bucketing 让 AllReduce 与反向计算重叠。

**公式与量级**

```
每卡训练状态显存 = 16 × Ψ（与卡数 N 无关，完整复制）
  例：7.5B 模型 → 120 GB/卡，单卡放不下
每卡梯度通信量 ≈ 2M（Ring AllReduce）
对应 ZeRO-0（无任何分片）。
```

**与 FSDP 的区别**
DDP 每卡存完整训练状态（冗余）；FSDP 把参数/梯度/优化器状态分片到 N 卡，用时 AllGather 临时拼回。DDP 通信少(1次AllReduce)但费显存；FSDP 通信多约 1.5 倍但每卡显存降到 1/N。模型能装进单卡→DDP；装不下→FSDP。

**常见误区**
以为 DDP 能训练超大模型：不能，它每卡都要装完整模型，模型超单卡就必须换 FSDP/TP/PP。
- 关联：implements→AllReduce; contrasts→FSDP; related→Distributed Training Communication

### Distributed Training Communication  (掌握度 L1)
- 别名：大模型训练通信方式, 集合通信, Collective Communication

**一句话结论**
大模型训练中的通信只有两大类：集合通信(Collective)和点对点通信(P2P)。集合通信是“一群 GPU 一起参与”(AllReduce/AllGather/ReduceScatter/All-to-All/Broadcast)，由 NCCL 实现；点对点是“一张卡发给另一张卡”(Send/Recv)，主要用于流水线并行传激活。

判别口诀：哪种并行策略，决定用哪种通信。DP→AllReduce；FSDP→ReduceScatter+AllGather；TP→AllReduce/AllGather；PP→P2P；MoE→All-to-All。几乎所有通信都能且应与计算 overlap。

**地基：通信走哪条物理链路**

```
链路                  典型单向带宽        用途
NVLink/NVSwitch(机内) ~450 GB/s (H100)   同机 8 卡，TP 命脉
PCIe(机内)            ~64 GB/s (Gen5)    GPU-CPU、offload
IB/RoCE(跨机 RDMA)    ~50 GB/s (400Gbps) 跨节点，PP/DP 通信
以太网                 更低                一般不用于训练热路径

核心认知：同一次 AllReduce，走 NVLink 和走跨机 IB 慢几个数量级。“哪种并行放机内、哪种跨机”是布局的头等大事。
```

**关键图：四大核心集合通信原语**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**AllReduce —— 数据并行命脉**
语义：每张卡有一份等长数据（通常是梯度），逐元素求和，结果每张卡都得到一份完整的和。

用在哪：DDP 梯度同步。N 卡各自在不同 mini-batch 上算梯度，反向后 AllReduce 得全局平均梯度，各自更新出一致参数。

例子：训练 Llama 用 DDP 起 128 卡，每卡吃不同数据，每 step 反向后对全部梯度(7B fp16=14GB)做一次 AllReduce。

通信量：Ring AllReduce 每卡 ≈ 2M，几乎与卡数 N 无关（能 scale 千卡的原因）。

能否 overlap：能，且是头等大事。反向逐层从后往前，某层梯度算完就能立刻 AllReduce，同时继续算前面层。PyTorch DDP 用 gradient bucketing 自动实现。

**ReduceScatter + AllGather —— FSDP/ZeRO 两把刀**
核心恒等式：AllReduce = ReduceScatter + AllGather，这是理解 FSDP 的钥匙。

ReduceScatter：各卡数据求和后按分片切开，每卡只留 1/N。
AllGather：每卡持一个分片，通信后每卡拿到拼接的完整数据。

用在哪：FSDP/ZeRO-3。前向/反向前用 AllGather 拼回分片参数；反向算完梯度用 ReduceScatter 求和并切片，每卡留 1/N。

为什么不用 AllReduce：AllReduce 后每卡都拿完整梯度仍冗余；ReduceScatter 让每卡只拿 1/N，配合分片优化器状态，显存降到 1/N。FSDP 就是把 DDP 的一次 AllReduce 拆成 ReduceScatter + 平时的 AllGather。

能否 overlap：能，靠 prefetch。算第 i 层时提前 AllGather 第 i+1 层参数；forward_prefetch/backward_prefetch 控制。

**All-to-All —— MoE 专属**
语义：最“拧巴”的一个。每张卡都持有要发给所有其他卡的不同数据块；通信后每张卡收到来自所有其他卡发给自己的块。本质是跨卡的“矩阵转置式重分布”。

用在哪：MoE 的 Expert Parallel。不同专家在不同卡上，token 经 router 后要发往选中专家所在的卡（dispatch 一次 All-to-All），专家算完再送回（combine 一次 All-to-All）。

例子：训练 Mixtral、DeepSeek-MoE，每个 MoE 层两次 All-to-All。专家跨机时走 IB，极易成瓶颈。

能否 overlap：能但更难。依赖 router 输出（先知道每个 token 去哪），依赖链紧。先进实现(DualPipe/Tutel)会把 dispatch 与其他专家/dense 计算重叠，工程复杂度高于 AllReduce overlap。

**P2P Send/Recv —— 流水线并行接力棒**
语义：点对点，rank i 把一块数据 Send 给 rank j，rank j Recv。只涉及两张卡。

用在哪：PP 的 stage 间传激活。模型按层切成若干 stage 放不同卡，前向时 stage k 算完把激活 Send 给 stage k+1；反向把梯度 Send 回 stage k。

例子：把 80 层切 8 个 stage，每 stage 10 层，激活沿流水线逐级 Send/Recv，配合 micro-batch 做 1F1B 调度。

通信特点：量相对小(只传激活)，但存在流水线气泡(bubble)——stage 间有依赖，启动收尾阶段部分卡闲置。

能否 overlap：能，这正是流水线调度核心。1F1B 让不同 micro-batch 的前向反向在不同 stage 交错，用一个 micro-batch 的计算掩盖另一个的 P2P 传输，压缩气泡。

**overlap 的统一判据**

```
能 overlap 的充要条件：
  发起通信 C 后，存在不依赖 C 结果的独立计算 X 可立刻做 → C 与 X 并行
反例（无法 overlap）：
  下一步计算立刻要用这次通信的结果 → 只能干等（暴露在关键路径）

对照：
  DDP AllReduce  → 易（反向逐层有独立计算）
  FSDP AllGather → 易（prefetch 下一层）
  TP AllReduce   → 难（下一步立刻要用，依赖紧 → 必须放 NVLink）
  PP P2P         → 靠 1F1B 调度
  MoE All-to-All → 能但需精心编排

物理下界：单步时间 ≥ max(总计算, 总通信)
```

**数值算例：感受通信量级**

```
DDP 训练 7B 模型，fp16 梯度，64 卡：
  梯度总量 M = 7e9 × 2 Byte = 14 GB
  Ring AllReduce 每卡通信量 ≈ 2M = 28 GB
  跨机 IB 有效带宽 ≈ 40 GB/s：
    T_comm ≈ 28 / 40 ≈ 0.7 s
  若单步计算 T_comp ≈ 1.0 s：
    无 overlap : 1.0 + 0.7 = 1.7 s
    完美 overlap: max(1.0,0.7) = 1.0 s → 加速约 1.7×

结论：通信占计算的比例(70%)决定 overlap 收益上限。
```

**五策略通信对照 + 布局原则**
DDP     : AllReduce            | 每step一次(分bucket) | 能overlap(bucketing)
FSDP    : AllGather+ReduceScatter| 每层多次            | 能overlap(prefetch)
TP      : AllReduce/AllGather   | 每层多次(极重)       | 难overlap(在关键路径)
PP      : P2P Send/Recv         | 每micro-batch一次    | 能overlap(1F1B)
MoE(EP) : All-to-All            | 每MoE层两次          | 能但复杂

布局原则：越重越频繁的通信放越快的链路。典型 3D 并行：
  TP → 机内 8 卡走 NVLink（每层通信最重）
  PP → 跨机（P2P 轻，IB 扛得住）
  DP/FSDP → 最外层跨机（AllReduce/AllGather 频率较低）

**常见误区**
1) 误以为 AllReduce 通信量随卡数线性增长：错，Ring 每卡趋近 2M，几乎与 N 无关。
2) 误以为 FSDP 比 DDP 通信更省：反了，FSDP 约 1.5 倍，省的是显存不是通信。
3) 把 TP 放跨机：严重错误，TP 每层通信、依赖紧、难 overlap，必须锁 NVLink 域内(≤8 卡)。
4) 以为开了 overlap 就一定生效：若通信 kernel 与计算抢 SM，或忘用独立 stream/pinned memory，overlap 名存实亡，必须 profiler 验证。
5) All-to-All 当廉价操作：MoE 跨机 All-to-All 常是瓶颈，专家负载不均会拥塞。
- 关联：prerequisite→Compute-Communication Overlap; related→FSDP; component→AllReduce; component→AllGather; component→ReduceScatter; component→All-to-All; related→Tensor Parallel; related→Pipeline Parallel

### Expert Parallel  (掌握度 L1)
- 别名：EP, 专家并行

**一句话结论**
Expert Parallel（EP，专家并行）：MoE 专用的并行维度，把不同的专家（expert）分布到不同卡上，每个 token 经 router 选择后被路由到它选中的专家所在卡计算。切的是“专家”。

**关键图：机制**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**机制**
每个 MoE 层：router 为每个 token 打分选 top-k 专家 → 一次 All-to-All(dispatch) 把 token 发往对应专家所在卡 → 专家前向 → 一次 All-to-All(combine) 把结果送回原位置。dense 部分通常仍用 FSDP/DP 分担。

**能否 overlap**
能但复杂：dispatch 依赖 router 输出，依赖链紧。DualPipe/Tutel 等会把 All-to-All 与其他专家或 dense 计算重叠。

**常见误区**
专家负载不均是核心难题：热门专家所在卡过载、冷门专家闲置，且跨机 All-to-All 昂贵，需要负载均衡损失和容量因子来缓解。
- 关联：implements→All-to-All; related→FSDP; related→Distributed Training Communication

### FP16  (掌握度 L1)
- 别名：Half Precision

**格式**

```
1 sign + 5 exponent + 10 mantissa；2Byte；最大65504；最小正规数约6.10e-5。
```

**主要风险**
大Activation/Gradient易Overflow，小Gradient易Underflow为0。

**Loss Scaling**

```
先放大Loss和Gradient，再在更新前Unscale；遇到Inf/NaN降低Scale并跳过更新。
```

**优势**
2Byte、Tensor Core成熟、在1附近尾数精度优于BF16。

**边界**
BF16预训练模型不应无脑转FP16微调；数值范围可能不兼容。
- 关联：related→Numerical Precision; contrasts→BF16; related→Mixed Precision Training

### FP8 Training  (掌握度 L1)
- 别名：FP8混合精度训练, E4M3/E5M2 Training

**双格式**
E4M3精度相对高、范围小，常用于前向；E5M2范围更大、精度低，常用于梯度。

**Scaling**

```
x_fp8=cast(x×scale)；恢复值约为cast_high(x_fp8)÷scale。单一全局Scale无法覆盖各层不同分布。
```

**Delayed与Current**
Delayed Scaling用历史Amax降低当前遍历开销；Current Scaling更及时；Microscaling用更小块减少Outlier影响。

**性能**
1Byte输入降低HBM与Tensor Core输入带宽，并提高支持硬件的GEMM吞吐；Cast/Scale、同步和回退算子会侵蚀收益。

**监控**
Amax、Saturation、Scale、Inf/NaN、逐层误差、Cast/Scale时间、Kernel覆盖率。

**硬件边界**
常依赖Hopper/Blackwell及Transformer Engine等软件栈；Accumulator精度需按具体Kernel确认。
- 关联：related→Numerical Precision; implements→Mixed Precision Training; related→CUDA

### FSDP  (掌握度 L1)
- 别名：Fully Sharded Data Parallel, 完全分片数据并行, ZeRO-3

**一句话结论**
FSDP（Fully Sharded Data Parallel，完全分片数据并行）的本质是：在数据并行的语义下，把每张卡上“完整复制一份模型训练状态”改成“每张卡只存 1/N 份参数、梯度和优化器状态”；在真正要用到某一层时，才临时用一次 AllGather 通信把这一层的完整参数拼回来，算完立刻丢掉。

它用通信换显存：把 DDP 里冗余复制的内存开销摊薄到 N 张卡上，从而能训练远超单卡显存的大模型。它是 ZeRO（Zero Redundancy Optimizer）思想在 PyTorch 中的原生实现。

**系统位置：它解决/不解决什么**
解决的核心问题：单卡装不下完整训练状态。一个 7.5B 模型混合精度+Adam 需 16×7.5e9 = 120GB，单张 80GB H100 都装不下，而 DDP 每张卡都存这 120GB，纯属冗余。

不解决：单层本身太大装不下（需 TP 切算子）；层数太多单卡放不下计算图（需 PP）。它减少的是显存不是计算量——每卡 FLOP 一点没少。

上下游：属于数据并行维度的增强版，可与 TP/PP/EP 正交组合成 3D/4D 并行，替代的是 DDP。

**直觉：共享工具间的工厂**
DDP：N 个工人每人一整套完整工具（全部参数/梯度/优化器状态），N 套占 N 倍仓库空间，极度浪费。

FSDP：N 个工人共用中央工具库，每人只保管 1/N 工具。轮到用某把扳手（某一层）时，保管它的工人广播复印给所有人（AllGather），大家一起用，用完立刻销毁复印件，只有原保管人留正本。

关键代价：每次用工具都要现场“复印+销毁”（通信+临时显存峰值）。类比失效点：现实中复印(AllGather)和干活(计算)可重叠——用当前扳手时提前复印下一把(prefetch)。

**关键图：单层参数生命周期时序**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**机制：一个训练 step 里做什么**
调度单位是 FSDP unit（通常一层）。

前向：1) 本地只存 1/N 参数分片；2) AllGather 拼回完整参数（临时）；3) 前向计算；4) 立即释放完整参数。

反向：5) 再次 AllGather（因为完整参数已被释放）；6) 反向计算得完整梯度；7) ReduceScatter 对梯度求和并按分片切回，每卡只留 1/N；8) 释放完整参数。

优化器更新：每卡用自己的 1/N 梯度+1/N fp32 参数副本+1/N 优化器状态，独立更新 1/N 参数。优化器状态全程分片、永不拼回，这是省显存最狠的一块。

与 DDP 通信对比：DDP 反向做 1 次 AllReduce；FSDP 做 前向AllGather + 反向AllGather + 反向ReduceScatter，通信量约 DDP 的 1.5 倍。

**公式与量级**

```
每参数训练状态 ≈ 16 Byte
  = fp16参数(2) + fp16梯度(2) + fp32副本(4) + 动量m(4) + 方差v(4)

每卡常驻训练状态（不含激活）：
  DDP        : M = 16 × Ψ            （完整复制，与 N 无关）
  FSDP ZeRO-3: M ≈ 16 × Ψ / N        （全部摊薄到 N 卡）

数值算例（Ψ=7.5B, N=64）：
  DDP  : 16 × 7.5e9        = 120 GB / 卡  → 放不下
  FSDP : (16 × 7.5e9) / 64 ≈ 1.875 GB / 卡 → 轻松放下

通信量：FSDP / DDP ≈ 3P / 2P = 1.5（多了前向 AllGather）

重要：以上只算参数相关状态，未含激活。FSDP 默认不分片激活，大 batch/长序列时激活可能才是 OOM 主因。
```

**最小 Sample：PyTorch FSDP**

```
from torch.distributed.fsdp import FullyShardedDataParallel as FSDP
from torch.distributed.fsdp import ShardingStrategy, BackwardPrefetch
from torch.distributed.fsdp.wrap import transformer_auto_wrap_policy
import functools, torch.nn as nn

# 关键点1：按 transformer block 切分 FSDP unit
policy = functools.partial(transformer_auto_wrap_policy,
            transformer_layer_cls={nn.TransformerEncoderLayer})

model = FSDP(
    model,
    auto_wrap_policy=policy,
    # 关键点2：FULL_SHARD=ZeRO-3（全分片）；SHARD_GRAD_OP=ZeRO-2
    sharding_strategy=ShardingStrategy.FULL_SHARD,
    # 关键点3：反向预取，让 AllGather 与反向计算重叠
    backward_prefetch=BackwardPrefetch.BACKWARD_PRE,
)
# 训练循环与 DDP 几乎一样，分片/拼回/释放由 FSDP 内部完成
for batch in loader:
    loss = model(batch).loss
    loss.backward()     # 内部自动 AllGather + ReduceScatter
    optimizer.step()    # 每卡只更新自己的 1/N 参数
```

**应用场景（何时用 FSDP）**
• 模型能装进单卡只想加速 → 用 DDP（FSDP 额外通信不划算）
• 训练状态超单卡但单层能装下 → 首选 FSDP
• 单层太大装不下 → FSDP + TP
• 层数极多想提利用率 → FSDP + PP
• MoE 大模型 → FSDP + EP
• 显存极紧 → FSDP + CPU offload

**常见误区**
1) 误以为 FSDP 减少计算量：错，只减显存，每卡 FLOP 与 DDP 一样。
2) 误以为用了 FSDP 显存就一定够：错，默认不分片激活，大 batch/长序列仍可能 OOM。
3) 把 FSDP 和 TP 混为一谈：FSDP 计算某层时拼回完整参数再算（层计算完整）；TP 是这一层计算本身被切开多卡协同。切分维度不同，可叠加。
4) 以为 ZeRO 和 FSDP 是两个东西：ZeRO 是 DeepSpeed 的算法思想，FSDP 是 PyTorch 原生实现，FULL_SHARD≈ZeRO-3。
5) 切分粒度随意设：太细通信次数暴涨，太粗临时参数撑爆显存峰值，需按 block 粒度并 profiler 调。
- 关联：prerequisite→Compute-Communication Overlap; contrasts→DDP; contrasts→Tensor Parallel; contrasts→Pipeline Parallel; implements→AllGather; implements→ReduceScatter

### GPUDirect  (掌握度 L1)
- 别名：GPUDirect RDMA, GPUDirect Storage

**GPUDirect RDMA**
NIC或PCIe Peer Device直接读写GPU Memory，常用于跨节点NCCL与GPU Serving。

**GPUDirect Storage**
NVMe/远程存储经DMA直接读写GPU Memory，避免CPU DRAM Bounce Buffer。

**收益**
减少CPU Memory Copy、CPU占用和数据路径长度，提高系统带宽并降低延迟。

**边界**
需要支持的GPU、NIC/Storage、驱动、内核、文件系统和PCIe拓扑；不满足可能回退到兼容路径。

**控制面**
绕过CPU数据Bounce不等于没有CPU控制；驱动/API仍由CPU设置与提交。
- 关联：related→CPU-GPU Communication; related→D2H; related→H2D

### H2D  (掌握度 L1)
- 别名：Host-to-Device, CPU到GPU传输

**定义**
Host Memory→Device Memory。训练Batch、推理输入、Checkpoint恢复和Offload回载是主要场景。

**执行路径**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**时间模型**

```
T_H2D≈T_latency+Bytes÷BW_effective。大块传输受带宽主导，小块传输受固定延迟主导。
```

**异步条件**
Pinned Host Buffer + cudaMemcpyAsync/non_blocking + 非默认Copy Stream + Copy Engine + 正确Event依赖。

**PyTorch**

```
loader=DataLoader(dataset,pin_memory=True)
for x in loader:
    x=x.to('cuda',non_blocking=True)
```

**关键风险**
Pinned源在DMA完成前不能被CPU修改或复用；Pageable路径可能经过内部Staging。
- 关联：related→CPU-GPU Communication; related→Pinned Memory; related→CUDA Streams

### Low-Bit Quantization  (掌握度 L1)
- 别名：低比特量化, INT8/INT4 Quantization

**量化公式**

```
q=clip(round(x÷scale)+zero_point)；x_hat≈scale×(q−zero_point)。
```

**粒度**
Per-Tensor、Per-Channel、Per-Group、Per-Token与Per-Block在元数据开销、Outlier适应和Kernel复杂度之间权衡。

**INT8**
常用于Weight+Activation推理、PTQ/QAT、KV Cache和部分通信。

**INT4**
常用于Weight-Only LLM推理，权重约0.5Byte/参数，但需要反量化与Scale。

**FP4**
裸E2M1极粗；NVFP4依赖16值微块Scaling、E4M3 Scale、FP32全局Scale、随机舍入与Hadamard等Recipe。

**性能边界**
压缩比不等于速度比；Decode可能受反量化、GEMV、KV Cache、调度和Kernel覆盖限制。
- 关联：related→Numerical Precision; related→PyTorch

### Megatron  (掌握度 L1)
- 别名：Megatron-LM, Megatron Core

**一句话结论**
Megatron-LM/Megatron Core 是 NVIDIA 的大规模 Transformer 训练框架，解决模型大到单卡单机放不下时如何高效切到成百上千张 GPU 训练。它是多卡编排层，建在 PyTorch 之上，不重写计算。

**关键图：AI 软件栈分层**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**提供的并行维度**
DP(数据切分,AllReduce)、TP(切算子内张量,NVLink)、PP(按层切 stage,P2P/1F1B)、VPP(细粒度交错,减 bubble)、CP(切序列)、EP(切 MoE 专家,All-to-All)、分布式优化器/FSDP(切优化器状态,ZeRO)。还有 CUDA Graph、激活重计算/offload、MoE、Transformer Engine(FP8)、checkpoint。

**与 PyTorch/CUDA 的关系**
模型仍是 nn.Module，张量仍是 torch.Tensor，通信走 torch.distributed/NCCL，kernel 仍是 CUDA。Megatron 决定模型怎么切、通信怎么排、流水线怎么调度。

**常见误区**
Megatron 不是 PyTorch 竞品；它不减少计算量，而是优化多卡编排。
- 关联：related→PyTorch; related→Pipeline Parallel; related→Virtual Pipeline Parallelism; related→Tensor Parallel

### Mixed Precision Training  (掌握度 L1)
- 别名：混合精度训练, AMP

**核心机制**
混合精度按算子和状态分配dtype，不是把模型整体cast到一种低精度。

**训练数据流**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**Loss Scaling**

```
L_scaled=L×S；g_scaled=S×g；更新前g=g_scaled÷S。FP16常用动态Loss Scaling，BF16通常可省。
```

**精度角色**
GEMM输入常为BF16/FP16/FP8；Accumulator、Softmax、Norm、Loss和Adam m/v常为FP32。

**PyTorch接口**

```
with torch.autocast(device_type='cuda', dtype=torch.bfloat16):
    loss = loss_fn(model(x), target)
loss.backward()
optimizer.step()
```

**边界**
内部累加精度取决于Kernel和后端；dtype标签不足以描述整个计算路径。
- 关联：related→Numerical Precision; related→PyTorch; related→CUDA

### Mixture of Experts  (掌握度 L1)
- 别名：MoE, Sparse Mixture of Experts, 混合专家

**一句话结论**
MoE 在 Transformer FFN 位置放置多个独立 Experts，由 Router 为每个 Token 只选择 Top-k 个。总参数量由全部 E 个 Experts 决定，每 Token 计算主要由激活的 k 个 Experts 决定，从而把参数容量与条件计算解耦；代价是动态负载、两次 All-to-All、小 GEMM、总参数显存和训练稳定性。

**Dense FFN 与 MoE 结构**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**统一 Shape 与参数例子**

```
B=2,S=3,T=6,H=8,E=4,k=2,F_expert=16,F_dense=32。Router logits [6,4]，Top-k indices/weights [6,2]，总 assignments=12。Dense参数=2×8×32=512；MoE experts总参数=4×2×8×16=1024，router=32；每Token激活专家参数=2×2×8×16=512，主MLP计算近似Dense。
```

**Route-Dispatch-Compute-Combine**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**Grouped GEMM 深入：从变长 Token 到 Tile Scheduler**
Grouped GEMM 先将同一 Expert 的 Token 打包到连续 packed_X[ΣT_e,H]，用 expert_offsets 和每组 A/B/C 指针、M_e/N/K 描述多个独立 GEMM。单个或少量 Persistent Kernel 将所有 Expert 输出切成 Tensor Core tiles；CTA 根据 prefix_tiles 把全局 tile_id 映射到 Expert，再加载该 Expert 的独立权重执行。它减少 launch、提高 tile 并行度并避免 pad-to-capacity 的无效 FLOP，但不能消除 Rank 间负载不均、热门 Expert 长尾和通信/GEMM 的 SM/HBM 争用。

**Grouped GEMM 打包与 Tile 调度图**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**Router 与 Top-k**
Router将X[T,H]投影为logits[T,E]，经softmax或其他评分函数选择Top-k，并对选中权重归一化。输出 y_t=Σ gate·Expert_e(x_t)。具体实现还可能使用sigmoid、group-limited routing、expert bias或aux-loss-free balancing。

**Capacity 与 Token Drop**

```
总assignments A=T×k；平均每Expert=A/E；Capacity C=ceil(T×k×capacity_factor/E)。超容量assignment可按概率drop；pad-to-capacity得到固定shape但浪费计算；dropless保留全部token但引入动态shape和负载不均。
```

**负载均衡与稳定性**

```
f_e=Expert e实际assignment比例；p_e=Router对Expert e的平均概率质量。经典辅助损失可写为L_aux=α×E×Σ f_e p_e；另有Router Z-Loss约束logsumexp(logits)。系数过小会塌缩，过大会妨碍专家专门化。
```

**p_e 的计算与 f_e 的区别**

```
常见定义：P_{t,e}=softmax(router_logits_t)[e]，p_e=(1/T)×Σ_t P_{t,e}。例：4 Token 对 E0/E1/E2 的概率分别为[0.7,0.2,0.1]、[0.6,0.3,0.1]、[0.2,0.7,0.1]、[0.1,0.6,0.3]，则p=[0.40,0.45,0.15]。Top-1硬选择为[E0,E0,E1,E1]，f=[0.5,0.5,0]。p是可微的软概率质量，f是离散的实际Assignment比例；Top-2时f的常见分母为T×k。
```

**Router Z-Loss：尺度、饱和与梯度**

```
Softmax对共同偏移不敏感：softmax(l+c)=softmax(l)，但Logit差值放大如[2,1,0]→[20,10,0]会使概率接近one-hot，p(1-p)趋近0，Router难以纠错。定义z_t=logsumexp(l_t)，L_z=λ_z×mean_t(z_t²)，梯度∂L_z/∂l_{t,e}=(2λ_z/T)×z_t×softmax(l_t)_e。Z-Loss约束主任务看不见的绝对尺度/共同偏移，并间接抑制极端Logits；它不能替代负载均衡，常与Router FP32、稳定logsumexp、合理初始化和必要的clipping配合。
```

**Expert Parallel 两次 All-to-All**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**Dispatch、Combine 与 Backward 的四次通信**
Forward Dispatch：按dst_rank统计send_counts，prefix-sum后Permute/Pack隐藏状态[A_local,H]，执行变长A2A，目标Rank再按local_expert分段。Forward Combine：Expert输出按origin_rank打包回传，Origin Rank用逆映射Unpermute并按Top-k权重scatter_add。Backward先把dY按Top-k拆分并A2A到Expert Owner，做Expert Backward，再把dX_assignment通过第二次A2A返回Origin；因此训练每个MoE层通常有4次大Payload交换，Expert参数若还有DP副本则另有梯度同步。

**MoE Chunk Pipeline 时间线**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**MoE overlap 的执行与观测要点**

```
for chunk in chunks:
  pack_done = permute_stream.pack(chunk)
  dispatch_done = comm_stream.wait(pack_done).all_to_all_async()
  gemm_done = compute_stream.wait(dispatch_done).grouped_gemm()
  combine_done = comm_stream.wait(gemm_done).all_to_all_async()
  permute_stream.wait(combine_done).unpermute_weighted_sum()

必须保证：不同chunk使用独立buffer；所有rank collective顺序完全一致；空chunk不能单边跳过；buffer在异步操作完成前不能复用。观测raw/exposed dispatch-combine、overlap时GEMM/通信膨胀、tokens-per-expert max/mean/P99、per-rank bytes、SM/Tensor Core/HBM/NVLink/IB与pipeline tail。
```

**EP 通信量算例**

```
T_local=4096,H=4096,BF16=2B,k=2,EP=8。一次dispatch远端发送≈T_local×k×H×2×7/8=58,720,256B=56MiB；combine再约56MiB，所以Forward约112MiB/Rank/MoE层，未含元数据、接收、padding和backward。
```

**Grouped GEMM 与计算碎片**
每个Expert收到动态T_e，逐Expert GEMM会产生大量小M维GEMM和launch。Grouped GEMM将多个专家的变长GEMM编组执行，改善Tensor Core利用率，但不能消除Rank间负载不均。

**Shared Experts 与细粒度 Experts**
Shared Experts对所有Token执行以承载通用知识；Routed Experts学习差异化知识，也可与A2A overlap。Fine-grained expert segmentation把N个大专家拆成mN个小专家并激活mK个，保持近似激活宽度同时增加组合灵活性，但使GEMM、路由和通信更碎。

**最小 PyTorch 机制**

```
logits=router(flat)                 # [T,E]
probs=softmax(logits,-1)
w,idx=topk(probs,k,dim=-1)         # [T,k]
for expert_id, expert in enumerate(experts):
    token_idx,slot_idx=where(idx==expert_id)
    out=expert(flat[token_idx])
    output.index_add_(0,token_idx,out*w[token_idx,slot_idx,None])
```

**训练与推理差异**
训练需要Router/Expert梯度、Aux/Z loss、Forward+Backward A2A、Optimizer状态；Prefill token多，GEMM较大；Decode每步token少，Expert GEMM碎且A2A延迟难摊薄，TPOT、热门专家尾延迟和全部Expert权重显存更突出。

**监控与失败模式**
重点监控tokens-per-expert、max/mean、router entropy、drop/overflow、dispatch/combine exposed time、per-rank bytes、grouped GEMM、per-expert M、MFU和peak memory。常见失败：expert collapse、capacity过小或padding过大、EP跨慢网络、专家过细、aux过强、decode batch过小。

**关键总结**
MoE通过条件激活扩大参数容量，但把Dense模型的规则GEMM问题转化为动态路由、负载均衡、Token重排、All-to-All和碎片化GEMM问题。分析时同时看Architecture、Routing、Compute、Communication、Memory和Serving。
- 关联：enables→Expert Parallel; implements→All-to-All; related→Megatron; related→PyTorch; component→Expert Parallel; component→All-to-All; enables→Compute-Communication Overlap

### Multi-Dimensional Parallelism  (掌握度 L1)
- 别名：3D Parallelism, 4D Parallelism, 5D Parallelism, 多维并行

**一句话结论**
DP/DDP切Batch，FSDP在DP语义下切模型状态；TP切单层Tensor；PP/VPP切Layers/Chunks；CP切Sequence；EP切MoE Experts。模型并行用于让模型/激活放得下，DP用于扩大吞吐；组合时每个Rank同时属于多个独立Process Groups。

**并行维度总览**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**统一比较**
DP通信为梯度AllReduce；FSDP为参数AllGather+梯度ReduceScatter；TP每层AR/AG/RS；PP传Activation/Gradient P2P；CP交换KV并归约dKV；EP做Dispatch/Combine两次All-to-All。TP/CP/EP通信频繁，应优先映射高速互联；PP/DP更适合跨节点。

**64卡五维布局**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**World Size与Rank坐标**

```
TP=2,PP=2,CP=2,EP=2,DP=4 → World=64。教学Rank公式：rank=((((dp×2+pp)×2+cp)×2+ep)×2+tp)。rank0的TP/EP/CP/PP/DP组分别为{0,1}/{0,2}/{0,4}/{0,8}/{0,16,32,48}。
```

**统一模型与Shape**

```
B_global=8,S=8,H=16,L=8,E=4,Top-2。DP4→B_local=2；CP2→[2,4,16]；TP2→4个Q Heads每Rank 2个、W1[16,64]→[16,32]；EP2→每Rank 2 Experts，本地逻辑Token=8，Assignments=16；PP2→每Stage 4 Layers。
```

**一个训练Step**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**DP/FSDP**
DDP复制模型并切Batch，Backward后同模型Shard在DP组AllReduce；FSDP分片参数/梯度/优化器状态，计算前参数AllGather，Backward后梯度ReduceScatter。DDP适合状态能放单卡；FSDP适合训练状态超单卡。

**TP**
TP使用Column/Row Parallel切Linear、Heads和Hidden，单层参数与计算约降1/TP，但每层高频通信且下一算子依赖紧；适合单层放不下和大Hidden，优先机内NVLink。

**PP/VPP**
PP把Layers分Stage，以Microbatch和1F1B流水，边界P2P传Activation/Gradient；VPP再切Chunks减少Bubble但增加P2P。适合深模型和跨节点模型扩展。

**CP**
CP把输入和全部Activation沿Sequence切分，非Attention模块本地执行；Attention本地Q需要完整KV，通过Ring/AllGather交换，Backward归约dKV。适合长上下文Activation OOM，与只切部分非Attention激活的SP不同。

**EP**
EP把MoE Experts分到不同Rank；Router后Token通过Dispatch All-to-All到Expert Owner，Grouped GEMM后Combine All-to-All返回。适合MoE Expert参数扩展，主要风险是动态负载和跨节点A2A。

**选择原则**
先判断单层→TP、总深度→PP、长序列→CP、MoE专家→EP、训练状态→FSDP；满足显存后尽量最小化模型并行并增加DP。结合拓扑与Profiler调整，避免小GEMM和暴露通信。

**配置示例**

```
--tensor-model-parallel-size 2
--pipeline-model-parallel-size 2
--context-parallel-size 2
--expert-model-parallel-size 2
--num-experts 4
--moe-router-topk 2
--sequence-parallel
--moe-grouped-gemm
--moe-token-dispatcher-type alltoall
--use-megatron-fsdp
--data-parallel-sharding-strategy optim_grads_params
```
- 关联：component→DDP; component→FSDP; component→Tensor Parallel; component→Pipeline Parallel; component→Virtual Pipeline Parallelism; component→Context Parallelism; component→Expert Parallel

### NCCL  (掌握度 L1)
- （本节点暂无详细内容，仅有摘要）

### NUMA  (掌握度 L1)
- 别名：Non-Uniform Memory Access

**机制**
多Socket系统中每个GPU通常靠近特定PCIe Root Complex与NUMA Node；远端DRAM需经过UPI/Infinity Fabric。

**优化**
将CPU Worker、Pinned Buffer和GPU绑定到相近NUMA节点；绑定后First-Touch分配，再注册Pinned。

**工具**

```
nvidia-smi topo -m
numactl --cpunodebind=0 --membind=0 python train.py
```

**指标**
H2D/D2H带宽、NUMA Miss、UPI流量、DataLoader等待和尾延迟。
- 关联：related→CPU-GPU Communication; related→Pinned Memory

### Numerical Precision  (掌握度 L1)
- 别名：数值精度, 大模型精度

**一句话结论**
低精度减少张量字节数、HBM流量和通信量，并可提高Tensor Core吞吐；代价是范围或精度下降。现代LLM使用混合精度：低精度做大GEMM，高精度做累加、敏感算子和优化器状态。

**BF32术语澄清**
BF32不是主流PyTorch/CUDA统一标准；通常应区分FP32、TF32、BF16、FP16、FP8。

**位布局与范围精度**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**格式总表**
FP32=1/8/23；TF32保8位指数、约10位尾数用于矩阵计算；BF16=1/8/7；FP16=1/5/10；FP8分E4M3与E5M2；INT8/INT4需要Scale；FP4训练依赖微块Scaling与专用Recipe。

**混合精度训练数据流**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**显存与状态口径**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**7B权重手算**

```
FP32=28GB；BF16/FP16=14GB；FP8/INT8=7GB；4bit=3.5GB。经典混合精度Adam按16Byte/参数约112GB，仅指参数相关训练状态。
```

**Activation手算**

```
[B=2,S=4096,H=8192]共67,108,864元素：FP32=256MiB，16bit=128MiB，FP8=64MiB。
```

**性能影响**
低位宽减少HBM与通信payload，并提高支持格式的Tensor Core吞吐；端到端收益受Amdahl定律、非GEMM算子、Cast/Scale、通信和Shape约束限制。

**稳定性风险**
主要风险是Overflow、Underflow、Rounding、Accumulation Error。需监控Loss、Grad Norm、Inf/NaN、Loss Scale、Amax、Saturation与逐层误差。

**训练与推理选型**
预训练默认BF16；FP16需GradScaler；Hopper/Blackwell可评估FP8；推理常用BF16/FP16、FP8/INT8或INT4 Weight-Only；FP4依赖新硬件与Recipe。

**关键误区**
BF16不是全面比FP16精确；TF32不节省FP32存储；FP8不自动让总训练显存减半；INT4不保证端到端快4倍；FP32累加也不能恢复输入量化丢失的信息。
- 关联：component→Mixed Precision Training; component→BF16; component→FP16; component→FP8 Training; component→Low-Bit Quantization; related→CUDA; related→PyTorch

### OpenAI Triton  (掌握度 L1)
- 别名：Triton, triton-lang

**一句话结论**
OpenAI Triton 是并行编程的语言和编译器，让你用 Python 语法写高性能 GPU kernel 而不写 CUDA C++。它是 torch.compile/Inductor 默认的 GPU 代码生成后端。

**编程模型**
按 block(program) 粒度写代码，thread 级细节(shared memory、索引、合并访问)交给编译器。心智差异：CUDA 写每个 thread 做什么，Triton 写每个 program(一块数据) 做什么。

**关键图：torch.compile 执行路径**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**最小示例**

```
import triton, triton.language as tl
@triton.jit
def add_kernel(x_ptr,y_ptr,out_ptr,n,BLOCK: tl.constexpr):
    pid=tl.program_id(0)
    offs=pid*BLOCK+tl.arange(0,BLOCK)
    mask=offs<n
    x=tl.load(x_ptr+offs,mask=mask)
    y=tl.load(y_ptr+offs,mask=mask)
    tl.store(out_ptr+offs,x+y,mask=mask)
```

**与 CUDA 的关系**
Triton 是 CUDA 之上的 kernel 语言/编译器，生成的 kernel 最终仍编译并 launch 到 CUDA。它替代的是手写 CUDA C++ 的繁琐，不是 CUDA 平台本身。

**常见误区**
不要与 NVIDIA Triton Inference Server(推理服务器) 混淆，二者只是重名。Triton 也不取代 CUDA。
- 关联：implements→CUDA; related→PyTorch; component→torch.compile

### Pinned Memory  (掌握度 L1)
- 别名：Page-Locked Memory, 锁页内存

**Pageable对比**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**机制**
Page-locked保证物理页稳定，避免Pageable→内部Pinned Staging，为真正异步传输和Overlap提供基础。

**API**

```
cudaHostAlloc(&p,bytes,cudaHostAllocDefault);
cudaHostRegister(existing,bytes,0);
# PyTorch
x=torch.empty(shape,pin_memory=True)
```

**代价**
占用不可分页RAM；分配/注册昂贵；过多会损害系统。推荐有限Pinned Buffer Pool长期复用。

**DataLoader**
DataLoader(pin_memory=True)在后台Pin线程准备Batch，优于训练主线程每批调用pin_memory()。

**生命周期**
异步H2D未完成时CPU不能改写或复用Pinned源；取消注册/释放前必须确认相关Stream完成。
- 关联：enables→H2D; enables→D2H; related→CPU-GPU Communication

### Pipeline Parallel  (掌握度 L1)
- 别名：PP, 流水线并行

**一句话结论**
Pipeline Parallel（PP，流水线并行）：把模型按层（深度方向）切成若干连续的 stage，分别放在不同卡上，激活像流水线一样在 stage 间用 P2P Send/Recv 逐级传递。切的是“层”。

**关键图：机制**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**机制**
前向时 stage k 算完把激活 Send 给 stage k+1；反向时把梯度 Send 回 stage k。把一个 batch 拆成多个 micro-batch 送入流水线，让各 stage 尽量同时有活干。

**流水线气泡与 1F1B**

```
气泡占比（朴素调度）≈ (P-1)/(M+P-1)
  P = stage 数（流水线深度）
  M = micro-batch 数
→ M 越大，气泡占比越小。

1F1B(one-forward-one-backward)调度：让不同 micro-batch 的前向、反向在不同 stage 交错进行，用一个 micro-batch 的计算掩盖另一个的 P2P 传输，压缩气泡。
```

**能否 overlap**
能，这正是流水线调度的核心。P2P 通信量小，1F1B 让计算与相邻 stage 的通信、以及不同 micro-batch 的前后向充分交错。

**常见误区**
1) micro-batch 太少：气泡占比大，流水线利用率低。
2) 把 PP 当成能省单层显存：PP 按 stage 分层，单层仍完整放在一张卡上，单层太大要靠 TP。
- 关联：related→Distributed Training Communication; contrasts→FSDP

### PyTorch  (掌握度 L1)
- 别名：torch

**一句话结论**
PyTorch(torch) 是支持 GPU 的深度学习张量库，是写模型的主语言。它不自己实现 GPU 计算，而是把算子分派到 cuBLAS/cuDNN/NCCL 或自带 CUDA kernel：PyTorch 是指挥，CUDA 是执行。

**核心组成**
torch.Tensor、autograd(自动微分)、nn.Module、optim、torch.distributed(DDP/FSDP/pipelining)、torch.cuda、torch.profiler、torch.compile。

**Eager vs Compiled**
Eager 每个算子立即启动预编译 CUDA kernel，灵活但 launch/HBM 往返多；torch.compile 捕获图后融合优化再执行，通常快很多。

**最小示例**

```
import torch
x = torch.randn(2,4096,4096, device='cuda')
w = torch.randn_like(x); b = torch.randn_like(x)
y = torch.sigmoid(x*w + b)   # Eager 约 3 次 kernel launch
print(y.shape)
```

**常见误区**
PyTorch 直接在 GPU 上算是误解；Megatron 不是 PyTorch 竞品而是建在其上的多卡编排层。
- 关联：implements→CUDA; enables→OpenAI Triton; related→Megatron

### ReduceScatter  (掌握度 L1)
- 别名：规约散射

**一句话结论**
ReduceScatter（规约散射）：各卡数据先逐元素求和，然后按分片切开，每张卡只保留自己负责的那 1/N 段。= Reduce(求和) + Scatter(散开)。

**关键图：数据流**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**机制与用途**
用在哪：FSDP/ZeRO-3 反向。算完完整梯度后用 ReduceScatter 求和并切片，每卡只留 1/N 梯度，配合分片的 fp32 参数副本和优化器状态，显存直接降到 1/N。

对比 AllReduce：AllReduce 后每卡都拿完整梯度仍冗余；ReduceScatter 让每卡只拿 1/N，省掉 (N-1)/N 的冗余存储。

**公式与恒等式**

```
每卡通信量 ≈ (N-1)/N × M ≈ M

核心恒等式：AllReduce = ReduceScatter + AllGather
  → FSDP 就是把 DDP 的一次 AllReduce，拆成 ReduceScatter(省梯度显存) + 平时的 AllGather(省参数显存)。
```

**能否 overlap**
能，可与反向计算重叠：某层完整梯度算完即可对它做 ReduceScatter，同时继续反向前面层。

**常见误区**
误以为 ReduceScatter 比 AllReduce 通信更贵：单次约 M，是 AllReduce(2M) 的一半；FSDP 通信总量多是因为多了前向那次 AllGather，而非 ReduceScatter 本身贵。
- 关联：component→Distributed Training Communication; enables→FSDP; related→AllReduce

### Tensor Parallel  (掌握度 L1)
- 别名：TP, 张量并行

**一句话结论**
Tensor Parallel（TP，张量并行）：把单个算子内部的大张量（如一个大矩阵乘的权重）按列或行切到多张卡上，多卡协同完成这一层的一次前向/反向。切的是“算子内的张量”，不是数据也不是层。

**关键图：机制**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**机制**
以 MLP 为例（Megatron 风格）：第一个线性层按列切权重（column-parallel），各卡算出输出的一部分；第二个线性层按行切（row-parallel），最后用一次 AllReduce 把部分和合并成完整输出。一层内通常有多次通信。

**公式与量级**

```
每层每次前向的通信量与激活大小同阶：
  ≈ O(B × S × H) 的 AllReduce/AllGather
通信频率极高（每层前后向各若干次），因此对带宽和延迟极敏感。
```

**为什么必须 NVLink**
TP 的通信在关键路径上：一层输出规约完，下一步立刻要用这个完整激活，依赖极紧，几乎无独立计算可 overlap。所以必须放在机内 NVLink 域（~450GB/s，通常≤8卡），跨机 IB(~50GB/s)会让它慢到不可用。

**与 FSDP 的区别**
FSDP 计算某层时把该层参数拼回完整再算（层的计算是完整的、在一张卡上）；TP 是这一层的计算本身被切开、多卡协同完成一次前向。切分维度不同，二者可叠加（TP 切算子 + FSDP 切数据）。

**常见误区**
1) 把 TP 跨机部署：严重错误，通信会成为绝对瓶颈。
2) 把 TP 和 FSDP 混为一谈：切分维度根本不同（算子内张量 vs 数据+状态分片）。
- 关联：implements→AllReduce; implements→AllGather; contrasts→FSDP; related→Distributed Training Communication

### Unified Memory  (掌握度 L1)
- 别名：CUDA Managed Memory, 统一内存

**定义**
cudaMallocManaged分配CPU和GPU均可寻址的内存；统一寻址不等于物理传输消失。

**迁移**
GPU访问CPU驻留页面可触发Page Fault和迁移；CPU/GPU反复写同一页面可能Thrashing。

**Prefetch**

```
cudaMemPrefetchAsync(ptr,bytes,gpu_id,stream);
cudaMemPrefetchAsync(ptr,bytes,cudaCpuDeviceId,stream);
```

**适合**
编程便利、不规则数据、超额使用GPU内存、CPU-GPU一致性平台。

**不适合**
可预测高吞吐热路径若访问模式清楚，显式批量H2D/D2H通常更可控。
- 关联：contrasts→CPU-GPU Communication; related→H2D; related→D2H

### Virtual Pipeline Parallelism  (掌握度 L1)
- 别名：VPP, 虚拟流水线并行, Interleaved Pipeline Parallelism

**一句话结论**
VPP（Virtual Pipeline Parallelism，虚拟流水线并行）不是增加 GPU 数，而是把每个物理 pipeline stage 上的连续层再切成 v 个更小的 model chunks，让同一张 GPU 在调度上扮演多个逻辑 stage，并用 interleaved 1F1B 把这些 chunk 与不同 microbatch 的前后向交错执行。理想情况下，pipeline bubble 相对普通 1F1B 缩小约 v 倍；代价是 P2P 通信次数/总量约增加 v 倍、调度更复杂，并且收益依赖 stage 均衡和通信能被隐藏。

**系统位置：VPP 解决什么**
普通 Pipeline Parallelism（PP）把模型按层切成 p 个物理 stage，每张 GPU 只负责一个连续层块。即使使用内存友好的 1F1B，流水线启动时仍要 warm-up、结束时仍要 cool-down，因此存在 bubble。VPP 不改变模型数学结果、不改变物理 GPU 数、不替代 TP/DP/FSDP；它是在 PP 内部进一步细化 stage 并优化调度，主要解决流水线粒度太粗导致的 bubble。

**关键图：普通 PP 与 VPP 的层映射**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**模型如何切分**
统一例子：L=16 个 Transformer layers，p=4 个物理 pipeline stages，v=2 个 model chunks/GPU。普通 PP 每卡 4 层：GPU0=L0–L3，GPU1=L4–L7，GPU2=L8–L11，GPU3=L12–L15。VPP 把每卡 4 层再分成两个 2 层 chunk：GPU0 持 L0–L1 和 L8–L9；GPU1 持 L2–L3 和 L10–L11；GPU2 持 L4–L5 和 L12–L13；GPU3 持 L6–L7 和 L14–L15。逻辑网络顺序没有改变，只是物理 GPU 0 在逻辑上同时扮演 virtual stage 0 和 4。

**深度补充：结论与统一假设**
普通 PP 把模型切成 p 个连续物理 stage；1F1B 通过 warm-up/steady/cool-down 交错前后向，主要减少 Activation 生命周期，经典理论 Bubble 与 GPipe 相同；VPP 把每个物理 stage 切成 v 个 chunks，使不可避免空档的粒度从完整 stage 时间缩小到 chunk 时间，Bubble 理想缩小 v 倍，但 Useful 不变。统一例子：p=4,m=8,v=2,t_f=t_b=1。

**普通 PP 结构与双向数据流**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**普通 PP、Microbatch 与 Bubble 来源**
16层模型切为GPU0:L0-L3、GPU1:L4-L7、GPU2:L8-L11、GPU3:L12-L15。Forward 发送边界 Activation，Backward 反向发送 Activation Gradient。流水线开始时后级 stage 没有输入，结束时梯度还要逐级返回，因此分别产生 p-1 个 forward 和 p-1 个 backward 依赖间隔。

**1F1B 的三阶段运行**
1F1B 分为 Warm-up、Steady State、Cool-down。Stage s 的 warm-up 数近似 w_s=p-s-1；p=4 时各 stage 分别为3/2/1/0。Steady State 中一个较新 microbatch 的 Forward 与一个较早 microbatch 的 Backward 交替；完成 Backward 后即可释放对应 Activation。

**普通 1F1B 精确时隙图：p=4,m=8**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**普通 PP Bubble 公式推导**

```
T_useful=m(t_f+t_b)。Forward Fill=(p-1)t_f，Backward Drain=(p-1)t_b，所以 T_bubble=(p-1)(t_f+t_b)，T_total=(m+p-1)(t_f+t_b)。Bubble/Useful=(p-1)/m；Bubble/Actual=(p-1)/(m+p-1)；Utilization=m/(m+p-1)。p=4,m=8,t_f=t_b=1 时 Useful=16、Bubble=6、Total=22、Bubble/Actual=27.27%、利用率=72.73%。
```

**为什么 GPipe 与普通 1F1B Bubble 相同**
1F1B 提前开始 Backward，缩短 Activation 生命周期，使保存量从约 O(m) 降到 O(p)；但 Forward 仍要穿过 p-1 个 stage、Backward 仍要返回 p-1 个 stage，首尾依赖长度不变，所以经典理想 Bubble 与 GPipe 相同。

**VPP 分块映射与 Bubble 缩减**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**为什么 VPP Useful 不变**

```
每个 chunk 的 Forward/Backward 时间约为 t_f/v、t_b/v；每张物理 GPU 仍执行 v 个 chunks，所以每 microbatch 的物理 GPU 有效计算=v(t_f/v+t_b/v)=t_f+t_b。对 m 个 microbatches：T_useful_vpp=m(t_f+t_b)，不变。
```

**为什么 VPP Bubble 约缩小 v 倍**

```
Interleaved 1F1B 用其他 chunk/microbatch 的 ready task 填充大空档，剩余边缘空档以 chunk 时间计：T_bubble_vpp=(p-1)(t_f+t_b)/v。Bubble/Useful=(p-1)/(mv)；Bubble/Actual=(p-1)/(mv+p-1)；Utilization=mv/(mv+p-1)。p=4,m=8,v=2 时 Useful=16、Bubble=3、Total=19、Bubble/Actual=15.79%，理想吞吐提升22/19≈1.158×。
```

**为什么不是 pv−1 与真实代价**
pv 描述单个 microbatch 穿越的逻辑虚拟 stages 和通信边界；Batch Bubble 衡量多个 microbatches 交错后每张物理 GPU 时间线的未填充空档。额外虚拟路径与其他 ready task 交错，不会全部串行暴露。代价是P2P通信量约增v倍；真实时间还要加暴露通信、stage不均衡和调度开销。

**1F1B 简化伪代码**

```
warmup = min(p-stage_id-1, m)
for i in range(warmup): forward(i)
for i in range(warmup, m):
    forward(i)
    backward(i-warmup)
for old in range(m-warmup, m): backward(old)
# 整个 microbatch group flush 后再 optimizer.step()
```

**深度补充：1F1B伪代码到真实调用**

_（此处为内嵌 SVG 图，请在 index.html 中查看）_

**伪代码逐行语义**
schedule_1f1b 为单个stage调度一个Step；m是microbatch数；warmup=min(p-stage_id-1,m)。Warm-up只Forward并把input/output引用放入FIFO；Steady每轮对新microbatch Forward，并从FIFO取最老microbatch Backward；Cool-down排空剩余FIFO。First stage不接收Forward输入，Last stage不发送Forward且从本地Loss开始Backward。

**真实Megatron API映射**

```
get_forward_backward_func()
  -> forward_backward_pipelining_without_interleaving(...)
P2PCommunicator.recv_forward / send_forward
schedules.forward_step(forward_step_func, ...)
input_tensors.append(input_tensor)
output_tensors.append(output_tensor)
deallocate_output_tensor(output_tensor, ...)
P2PCommunicator.send_forward_recv_backward(...)
backward_step(input_tensor, output_tensor, output_tensor_grad, config)
P2PCommunicator.send_backward_recv_forward(...)
```

**Activation与梯度生命周期**
stash_activation不是复制Tensor到独立缓存，而是FIFO保留input_tensor/output_tensor引用和PyTorch grad_fn。output发送后可伪释放output_tensor.data但保留grad_fn；收到下游dy后backward_step产生本stage参数梯度与dx。FIFO pop、Backward完成和局部引用释放后，完整Autograd上下文才可回收。

**最小真实Forward示例**

```
h = stage0(x)
h_recv = h.detach().requires_grad_(True)
stage1.set_input_tensor(h_recv)
pred = stage1()
loss = ((pred-target)**2).mean()
loss.backward()
dh = h_recv.grad
h.backward(dh)
# 跨进程时h数据由send/recv传输，Autograd graph不会跨rank自动传输。
```

**First/Middle/Last Stage职责**
First从Dataset读取Tokens并产生Hidden States；Middle通常从P2P接收Hidden States，Dataset字段可为None或仅有Packed Sequence元数据；Last从P2P接收Hidden States，同时本地取得Labels/Loss Mask，计算Loss。Megatron forward_step_func返回output_tensor和绑定当前microbatch信息的loss callback。

**真实实现的组合通信**
Steady state通常使用send_forward_recv_backward同时发送新Forward输出并接收旧microbatch的dy，再用send_backward_recv_forward同时发送dx并接收下一Forward输入。生产实现还包含Tensor Shape协议、梯度同步开关、Activation Checkpoint、VPP chunk选择、Multimodule与通信重叠。

**深度补充常见误区**
普通1F1B不会消除理论Bubble；(p-1)/m是Bubble相对Useful而非总时间占比；VPP的v个chunks各只有约1/v工作量，Useful不乘v；Bubble减半不等于训练速度翻倍；v越大通信和调度代价越高。

**通信代价与 overlap**
普通 PP 的每个物理 stage 边界，每个 microbatch 前向发送 activation、反向发送 activation gradient。VPP 把总逻辑 stage 数从 p 增加到 p×v，边界也增加，因此 NVIDIA 给出的结论是总 P2P 通信量约增加 v 倍。消息 tensor shape 通常仍是 [micro_batch, sequence, hidden]，不是每条消息缩小 v 倍；增加的是边界/消息次数。

可以 overlap：调度器可用异步 P2P send/recv，在某个 chunk 通信时执行本 GPU 另一个 chunk 或另一个 microbatch 的计算。但是否真重叠取决于 NCCL/P2P backend、CUDA stream、网络拓扑和 SM/显存带宽争用。若通信暴露时间超过节省的 bubble，继续增大 v 反而变慢。必须用 Nsight Systems/Megatron timers 看 timeline。

**显存影响**
VPP 不会像 FSDP 那样把参数、梯度、优化器状态降到 1/N；每张 GPU 仍持有与普通 PP 大致相同总层数，只是拆成多个不连续 chunks。参数显存基本不变。activation 显存由调度中同时在飞的 microbatches、chunk 数、recompute 策略决定：VPP 不是天然的显存优化，某些配置下 bookkeeping/通信 buffer/保存 activation 反而更复杂。1F1B 的核心内存优势是把 outstanding forward activations 从 O(m) 限制到与 pipeline 深度同阶；实际 VPP 峰值应以框架实现和 profiler 为准。

**Megatron 配置示例**

```
# Megatron Core / NeMo Bridge 风格（当前官方文档）
model_config = GPTModelProvider(
    num_layers=16,
    pipeline_model_parallel_size=4,
    virtual_pipeline_model_parallel_size=2,  # 每个物理 rank 2 个 chunks
)

# Megatron-LM 某些 CLI 版本使用“每个虚拟 stage 的层数”表达
--pipeline-model-parallel-size 4 \
--num-layers-per-virtual-pipeline-stage 2

# 本例：v = L / (p × layers_per_virtual_stage)
#       = 16 / (4 × 2) = 2

# 版本敏感：不同 Megatron/NeMo 版本参数名与约束可能不同，
# 以当前安装版本的官方 config/API 为准。
```

**实现约束与调优方法**
常见约束：层数要能被物理 stage 数与 virtual chunk 粒度整除；Megatron 某些版本要求 microbatch 数能被 pipeline parallel size 整除；部分旧实现对 p=2 的 interleaved schedule 有限制。调优建议：1) 先保证物理 stage 计算均衡；2) 固定 p,m，从 v=2 开始；3) 比较 bubble time、P2P exposed time、activation peak、step time；4) 只有 bubble 节省大于额外通信时才提高 v；5) TP 放机内 NVLink，PP/VPP 边界尽量按拓扑映射，避免高频跨慢链路往返。

**与相邻技术的区别**
普通 PP：每 GPU 一个连续 stage；VPP：每 GPU 多个不连续 chunks，interleaved 调度，bubble 更小但通信更多。
1F1B：是一类调度策略，普通 PP 与 VPP 都可用；VPP 常指 interleaved 1F1B。
Zero-Bubble Pipeline：通常进一步拆分 backward 的 input-gradient(B) 与 weight-gradient(W) 并重排，以逼近零 bubble；VPP 主要靠把 stage 切成 chunks，并不等于 zero-bubble。
Tensor Parallel：切单个算子张量；VPP 仍是按层深度切分。
FSDP/DP：切数据和训练状态；与 VPP 正交，可组成 TP×PP/VPP×DP/FSDP。

**什么时候应该用**
适合：已经必须使用 PP；普通 1F1B 的 profiler 显示 bubble 明显；microbatch 数受 global batch 或显存限制不能继续增大；P2P 链路足够快；模型层数足够多且能均匀切 chunk。
不适合：p 很小或 m≫p，原 bubble 已很低；网络慢、P2P 已是瓶颈；层数不能均匀切；stage 本身严重不均衡；显存极紧且 VPP 调度增加 activation/buffer 峰值。此时先解决负载均衡、拓扑映射、recompute 或减少通信。

**常见误区**
1) VPP 不是创建更多 GPU，也不是让一张 GPU 真正同时跑两个大 GEMM；它创建多个逻辑 stage，并通过时间调度提高利用率。
2) v 越大不一定越快：bubble 下降约 1/v，但通信量约增 v，存在最优点。
3) VPP 不等于显存分片：每卡总参数基本不变。
4) 不要混淆两种 bubble 百分比口径。
5) 理论公式忽略通信和不均衡；最终决策必须看真实 step time 和 timeline。

**关键总结**
VPP = PP 的更细粒度 stage 切分 + interleaved 1F1B。它让每张 GPU 持有 v 个 model chunks，用更短的 chunk 计算填补流水线等待；理想 bubble 缩小 v 倍，但 P2P 通信约增加 v 倍。选择 v 的本质是用更多通信换更少空闲时间，工程上必须测量 bubble 节省是否超过通信与调度开销。
- 关联：implements→Pipeline Parallel; related→Compute-Communication Overlap; prerequisite→Pipeline Parallel; implements→Megatron

### torch.compile  (掌握度 L1)
- （本节点暂无详细内容，仅有摘要）

## 教学事件

- [L0001] Compute-Communication Overlap (D2) — 用异步执行+多 stream+依赖管理，让计算掩盖通信/拷贝等待，理想总时间为 max 而非 sum
- [L0002] FSDP (D2) — 数据并行语义下把参数/梯度/优化器状态分片到N卡，用时AllGather临时拼回、用完即弃，用通信换显存
- [L0003] Distributed Training Communication (D2) — 通信分集合通信(NCCL)与点对点(P2P)两类；策略决定原语，几乎都能与计算overlap
- [L0004] AllReduce (D2) — 各卡数据求和后每卡都得到完整的和，用于 DDP 梯度同步，Ring 版每卡通信量约 2M
- [L0005] AllGather (D1) — 各卡分片拼成完整数据每卡都拿全，用于 FSDP 拼参数、TP 收激活
- [L0006] ReduceScatter (D1) — 求和后按分片切开每卡只留1/N，用于 FSDP 梯度规约并分片
- [L0007] All-to-All (D1) — 转置式重分布每卡把不同块发给不同卡，用于 MoE 的 token 路由
- [L0008] DDP (D1) — 每卡完整模型副本各吃不同数据，反向AllReduce同步梯度；最费显存实现最简
- [L0009] Tensor Parallel (D2) — 切单个算子内的张量多卡协同完成一层，通信重依赖紧必须机内NVLink
- [L0010] Pipeline Parallel (D2) — 按层切stage放不同卡，P2P传激活，用1F1B调度压缩流水线气泡
- [L0011] Expert Parallel (D1) — MoE专用，不同专家放不同卡，两次All-to-All路由token
- [L0012] Virtual Pipeline Parallelism (D2) — VPP 将每个物理 pipeline stage 再切成 v 个 model chunks，用 interleaved 1F1B 将理想 bubble 降低约 v 倍，代价是 P2P 通信约增加 v 倍。
- [L0013] CUDA (D2) — NVIDIA 并行计算平台与编程模型，提供 kernel/thread/block、内存层级、stream，是 GPU 计算底座
- [L0014] PyTorch (D2) — 为深度学习优化的 GPU 张量库，提供 Tensor/autograd/nn/optim/distributed，算子分派到 CUDA kernel 执行
- [L0015] OpenAI Triton (D2) — 用 Python 写 GPU kernel 的语言和编译器，torch.compile/Inductor 默认 GPU 代码生成后端，生成的 kernel 仍跑在 CUDA 上
- [L0016] Megatron (D2) — NVIDIA 大规模 Transformer 训练框架，提供 TP/PP/VPP/DP/CP/EP 等并行，建在 PyTorch 之上，是多卡编排层
- [L0017] CUDA (D2) — CUDA 性能由线程到 SM 的执行映射、warp 访存合并、片上数据复用和资源压力共同决定。
- [L0018] Virtual Pipeline Parallelism (D2) — 普通1F1B通过交错前后向降低Activation存储但不改变经典Bubble；VPP把stage切成v个chunks，使Bubble理想缩小v倍而Useful不变。
- [L0019] Virtual Pipeline Parallelism (D2) — 1F1B真实实现以P2PCommunicator、forward_step/backward_step和input/output FIFO管理新Forward与旧Backward；跨rank只传Tensor数据，不自动传Autograd Graph。
- [L0020] Mixture of Experts (D2) — MoE以Router为每个Token选择Top-k Experts，使总参数按E扩展而激活计算按k扩展；系统代价集中在动态负载、两次All-to-All、碎片化Expert GEMM和总参数显存。
- [L0021] Context Parallelism (D2) — CP沿Sequence切全部激活，通过KV Ring/AllGather和dKV归约解决Attention跨Token依赖，将长上下文激活显存约降到1/CP。
- [L0022] Multi-Dimensional Parallelism (D2) — 不同策略切Batch、模型状态、层内Tensor、Layers、Sequence和Experts；64卡例子用TP2×PP2×CP2×EP2×DP4展示Rank组、Shape与一个Step数据流。
- [L0023] Numerical Precision (D2) — 位宽决定存储与潜在吞吐，指数位决定范围、尾数位决定精度；训练依靠混合精度而非单一dtype。
- [L0024] Mixed Precision Training (D2) — 低精度负责GEMM和大张量，高精度负责累加、敏感操作与长期优化状态。
- [L0025] BF16 (D1) — BF16用8位指数保留FP32级范围，用7位尾数换取2Byte存储和Tensor Core吞吐。
- [L0026] FP16 (D1) — FP16用5位指数与10位尾数，局部精度优于BF16但范围窄，训练通常需要Loss Scaling。
- [L0027] FP8 Training (D2) — FP8通过E4M3/E5M2与逐张量或逐块Scaling加速GEMM并降低流量，但需要Amax、Scale和稳定性管理。
- [L0028] Low-Bit Quantization (D2) — 整数低比特格式需要Scale/Zero Point，把连续浮点张量映射到有限离散值，主要用于推理权重、激活和KV Cache。
- [L0029] CPU-GPU Communication (D2) — 独立GPU通过PCIe/NVLink-C2C等链路与CPU内存通信；核心优化是减少传输、使用Pinned DMA并通过Stream和双缓冲隐藏剩余传输。
- [L0030] H2D (D2) — H2D把Batch、参数或特征从Host DRAM送到GPU HBM，通常由Copy Engine经PCIe/NVLink-C2C执行。
- [L0031] D2H (D2) — D2H把结果、Checkpoint或Offload状态返回Host；异步D2H后CPU首次读取前必须同步对应Event。
- [L0032] Pinned Memory (D2) — Pinned Memory锁定物理页，使Copy Engine可直接DMA；应池化复用，避免过量锁页和频繁注册。
- [L0033] CUDA Streams (D2) — 同一Stream有序、不同Stream可并发；Event表达依赖，record_stream保护异步Tensor内存生命周期。
- [L0034] NUMA (D1) — Host Buffer若位于远端Socket，H2D/D2H会额外跨CPU互联，降低带宽并增加尾延迟。
- [L0035] Unified Memory (D2) — Unified Memory统一指针和迁移管理，但页面仍可能在CPU/GPU间迁移并产生Page Fault或Thrashing。
- [L0036] GPUDirect (D2) — GPUDirect允许NIC、Storage或Peer GPU直接DMA到GPU Memory，降低CPU占用、复制次数和延迟。
- [L0037] Mixture of Experts (D2) — 补全了变长 Grouped GEMM 的 Tile Scheduler、p_e 数值计算、Z-Loss 梯度，以及 MoE 前后向 A2A Chunk Pipeline 的依赖、争用和观测方法。
