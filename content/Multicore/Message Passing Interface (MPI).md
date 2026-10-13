---
updated_at: 2026-10-13T18:18:16.150+02:00
---
> **MPI (Message Passing Interface)** is a standard (implemented in multiple libraries, but we will use C's `mpi.h`) that prescribes how messages are passed between processes in [[architettura di Von Neumann|architectures]] that support **MIMD** (*Multiple-Instruction Multiple-Data*) [[parallelism]], where each core has a memory.

> It follows the **SPMD** (Single-Program Multiple-Data) paradigm, in which only one program is compiled and executed by multiple processes. The behaviour of each process is differentiated by an if-else on the process ID.

#todo pag. 7 pdf 2

# Programs
## Boilerplate

## Compilation and execution

## Debugging

# Elements

#todo make them each its own note
## Ranks

## Communicators

## Types

## Message matching

## MPI_Send message buffer

## Blocking and non blocking communication

## Point to point communication modes