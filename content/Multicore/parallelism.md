---
updated_at: 2026-10-13T18:13:28.990+02:00
---

> Parallelism can either concern **data** or **tasks**. Data parallelism consists in partitioning the data used in solving the problem among the cores, while task parallelism consists in partitioning the problem's task in sub-tasks, each processed by a core.

Efficient parallel programs must take care of those properties:

- **proper communication** between processes,
- **balancing the load** between process to reduce the probability of bottlenecks,
- **syncronizing** the work pace to not have processes too far ahead of the others.

# Types of parallel systems

|                                                                                                                                                                                                 | Shared Memory                    | Distributed Memory                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- | ----------------------------------- |
| **SIMD** (*Single-Instruction Multiple-Data*):<br><br>All cores share the control units, so at each time step they must all execute the same instruction or stay idle. That's the case of GPUs. | [[CUDA]]                         |                                     |
| **MIMD** (*Multiple-Instruction Multiple-Data*):<br><br>Each core has its independent control units                                                                                             | [[Pthreads]]/[[OpenMP]]/[[CUDA]] | [[Message Passing Interface (MPI)]] |
