---
updated_at: 2026-10-19T15:33:28.831+02:00
---
> **MPI (Message Passing Interface)** is a standard (implemented in multiple libraries, but we will use C's `mpi.h`) that prescribes how [[message|messages]] are passed between [[process|processes]] in [[architettura di Von Neumann|architectures]] that support **MIMD** (*Multiple-Instruction Multiple-Data*) [[parallelism]], where each core has a memory.

> It follows the **SPMD** (Single-Program Multiple-Data) paradigm, in which only one program is compiled and executed by multiple processes. The behaviour of each process is differentiated by an if-else on the process ID.

# MPI programs in C
## MPI boilerplate

```c
#include <stdio.h>
#include <mpi.h>

int main(int argc, char* argv[]) {
	MPI_Init(&argc, &argv);
	... // program portion with MPI calls
	MPI_Finalize();
	return 0;
}
```


> `int MPI_Finalize(void)` cleans up the allocated memory for MPI.

> The function `int MPI_Init(int* argc_p, char*** argv_p)` takes the program arguments as inputs and it implicitly defines a [[communicator]], called **MPI_COMM_WORLD**, which contains all the proccesses created at the start of the program.

## Compilation

```
mpicc -g -Wall -o executable_file_name_here source_file_name_here
```

- `mpicc` is the wrapper script
- `-g` produces debugging informations
- `-Wall` turns on all warnings

## Execution

```
mpiexec -n n_of_procs_to_run_the_executable_file_with executable_file
```

> Note: Each process is usually identified by a non negative integer called **rank**.