---
updated_at: 2026-10-19T16:37:19.923+02:00
---
> A **communicator is a collection of [[process|processes]] that can send message to each other**.

Example:

``` c
#include <stdio.h>
#include <mpi.h>

int main(void) {
	int comm_sz, my_rank;
	MPI_Init(NULL, NULL);
	MPI_Comm_size(MPI_COMM_WORLD, &comm_sz);
	MPI_Comm_rank(MPI_COMM_WORLD, &my_rank);
	printf(“hello, world from process %d out of %d\n”, my_rank, comm_sz);
	MPI_Finalize();
	return 0;
}
```

> `int MPI_Comm_size(MPI_Comm comm, int* comm_sz_p)` takes a communicator and a [[puntatore|pointer]] an integer, which value is set by the function to the number of processes in the communicator.

> `int MPI_Comm_rank(MPI_Comm comm, int* my_rank_p)`  takes a communicator and a pointer an integer, which value is set by the function to the rank of the process calling it.

New communicators can be created.