---
updated_at: 2026-10-20T21:26:27.939+02:00
---
> [[Message Passing Interface (MPI)]] supports **collective comunication**, an umbrella that describes every scenario that concerns the exchange of [[message|messages]] between more than two [[process|processes]] enabled by a native function.

# Functions

> Every collective communication function, called a **collective**, is called **by a single process**.

However the hood, each process computes and spreads intermediate results, typically following a tree or a butterfly pattern (MPI_Allreduce) to guarantee an execution [[complessità temporale|time]] of $O(\log_{2}(\text{n. of processes}))*\text{send/recv time}$.

https://scalable.uni-jena.de/opt/pc/chapters/assignment_mpi_collective.html

## MPI_Reduce

> This operation performs a reduction operation (e.g., sum, product, maximum) on data distributed across all processes. The result stored on a specified root process.

``` c
MPI_Reduce(
    const void* sendbuf,   // send buffer
    void* recvbuf,         // receive buffer (significant only at root)
    int count,             // number of elements in send buffer
    MPI_Datatype datatype, // datatype of elements
    MPI_Op op,             // MPI reduction operator
    int root,              // rank of the root process
    MPI_Comm comm          // communicator
);
```

## MPI_Bcast

> This operation sends a message from one process (the root) to all other processes in the [[communicator]].

``` c
MPI_Bcast(
    void* buffer,          // buffer (send at root, receive elsewhere)
    int count,             // number of elements in buffer
    MPI_Datatype datatype, // datatype of elements
    int root,              // rank of the root process
    MPI_Comm comm          // communicator
);
```

## MPI_Allreduce

> Similar to MPI_Reduce, but the result is broadcasted to all processes.

``` c
MPI_Allreduce(
    const void* sendbuf,   // send buffer
    void* recvbuf,         // receive buffer (puts result on all procs)
    int count,             // number of elements in send buffer
    MPI_Datatype datatype, // datatype of elements
    MPI_Op op,             // MPI reduction operator
    MPI_Comm comm          // communicator
);
```

#ai
## MPI_Scatter

> Takes data from a root process and distributes distinct chunks (segments) of equal size to each process in the communicator.

``` c
MPI_Scatter(
    const void* sendbuf,   // send buffer (significant only at root)
    int sendcount,         // number of elements sent to each process
    MPI_Datatype sendtype, // datatype of send buffer elements
    void* recvbuf,         // receive buffer
    int recvcount,         // number of elements in receive buffer
    MPI_Datatype recvtype, // datatype of receive buffer elements
    int root,              // rank of the root process
    MPI_Comm comm          // communicator
);
```

## MPI_Gather

> The inverse of MPI_Scatter, this operation collects data chunks from all processes and sends it to the root process.

``` c
MPI_Gather(
    const void* sendbuf,   // send buffer
    int sendcount,         // number of elements in send buffer
    MPI_Datatype sendtype, // datatype of send buffer elements
    void* recvbuf,         // receive buffer (significant only at root)
    int recvcount,         // n of elements received from *each* process
    MPI_Datatype recvtype, // datatype of receive buffer elements
    int root,              // rank of the root process
    MPI_Comm comm          // communicator
);
```

## MPI_Allgather

> Similar to MPI_Gather, but the combined/collected data is distributed to the receive buffers of **all** processes rather than just the root.

``` c
MPI_Allgather(
    const void* sendbuf,   // send buffer
    int sendcount,         // number of elements in send buffer
    MPI_Datatype sendtype, // datatype of send buffer elements
    void* recvbuf,         // receive buffer
    int recvcount,         // n of elements received from each process
    MPI_Datatype recvtype, // datatype of receive buffer elements
    MPI_Comm comm          // communicator
);
```

## MPI_Reduce_Scatter

> Combines values from all processes using a reduction operation and then scatters the resulting vector chunks across the processes (functionally equivalent to an MPI_Reduce followed by an MPI_Scatterv).

``` c
MPI_Reduce_Scatter(
    const void* sendbuf,     // send buffer
    void* recvbuf,           // receive buffer
    const int recvcounts[],  // array specifying number of result elements distributed to each process
    MPI_Datatype datatype,   // datatype of elements
    MPI_Op op,               // MPI reduction operator
    MPI_Comm comm            // communicator
);
```

## MPI_Alltoall

> A generalized data-movement operation where each process sends distinct data chunks to _every_ other process. Process $i$ sends the $j$-th chunk of its send buffer to process $j$, and receives the $i$-th chunk from process $j$ into its receive buffer (matrix transpose pattern).

``` c
MPI_Alltoall(
    const void* sendbuf,   // send buffer
    int sendcount,         // number of elements sent to each process
    MPI_Datatype sendtype, // datatype of send buffer elements
    void* recvbuf,         // receive buffer
    int recvcount,         // number of elements received from each process
    MPI_Datatype recvtype, // datatype of receive buffer elements
    MPI_Comm comm          // communicator
);
```