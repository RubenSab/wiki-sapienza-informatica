---
updated_at: 2026-10-20T16:40:26.055+02:00
---
> [[Message Passing Interface (MPI)]] enables the communication between [[process|processes]] through the functions `MPI_Send` and `MPI_Recv`.

# MPI_Send

Takes:
- a [[puntatore|pointer]] to the data buffer (OUT),
- the number of **elements** in each message (IN),
- the MPI data type of the message (MPI has wrappers of the most common types, like MPI_INT),
- the rank of destination process (IN),
- label identifying the message's type (IN),
- the [[communicator]] that contains both the sender process and the receiver (IN)
Returns an int.

> Note: Message sending in MPI is **nonovertaking**. This means that two messages sent from a same process arrive in the correct order, though there is no guarantee on the order of messages sent from different processes.

> Note: if a call to MPI_Send returns immediately after finding no matching receive, the message will be lost.

> Note: After the function returns, you can reuse the buffer, but it's not guaranteed even that the the data has left the sender.

## Related calls and Point-To-Point communication modes

| Function      | Communication mode employed             | Description                                                                                                                                                                                                 |
| ------------- | --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **MPI_Send**  | standard (locally or globally blocking) | If the message is small enough it behaves like **MPI_Bsend**, making it *locally* blocking, else it behaves like **MPI_SSend**, being *globally* blocking).<br>*MPI* provides the buffer.                   |
| **MPI_Bsend** | buffered (locally blocking)             | It unblocks the sending process and returns only once the message is copied in the receiver buffer.<br>The *user* provides the buffer.                                                                      |
| **MPI_Ssend** | syncronous (globally blocking)          | It unblocks the sending process and returns only after the destination process has a copy of the message in its buffer and has started the retrieval of the message.                                        |
| **MPI_Rsend** | ready (non-blocking)                    | It returns only if a matching receive function has already been called. Otherwise the function returns with an error code.<br>The purpose of this mode is to reduce the overhead of handshaking operations. |
| **MPI_Isend** | immediate (non-blocking)                | It returns immediately without ever blocking; the buffer is reusable only after **MPI_Wait**, **MPI_Test** or related functions.                                                                            |

## MPI_Isend: non-blocking Send

> MPI_Send is **blocking** (the caller process has to wait while the message copy is ready), while MPI_Isend is **non blocking** (also called *immediate*, meaning that it returns immediately upon initiating a transfer, so the process doesn't have to wait while the NIC is sending data).

Its signature is the same of Send, but, instead of the status argument, it has a pointer to the request (MPI_Request) (OUT). MPI_Request is an handle that can be queryied on the status of the operation.

## Implementation details

> Note: Fewer, larger messages are cheaper, because every message pays a fixed cost at the beginning.

### Underlying protocol

MPI can either use [[stack protocollare TCP-IP|TCP/IP]] [[socket|sockets]] (which are slower because the packet needs to pass through the kernel and be copied to be then passed to the NIC) or RDMA (which bypasses the kernel, lowering the latency).

### How does MPI make the buffer reusable?

#todo pag. 35-38

> Note: Don't assume that the send is done with eager and returns immediately for small buffers, or your code won't be portable.

# MPI_Recv

Takes:
- a pointer to the receive buffer (output),
- number of expected messages to receive
- the MPI data type of the message,
- rank of the sender process (optional, can be MPI_ANY_SOURCE),
- rank of this process (optional, can be MPI_ANY_TAG),
- pointer to the communicator that contains both the sender process and the receiver,
- the status (output), of type MPI_Status. It's a record type with fields MPI_SOURCE, MPI_TAG and MPI_ERROR.
  It can be MPI_STATUS_IGNORE.
Returns an int.

## MPI_Irecv: non-blocking Send

> MPI_Recv is **blocking** (meaning that it **blocks** (hangs) the process, making it listen until a matching message is received), while MPI_Irecv is **non blocking** (meaning that it returns immediately upon receiving).

Its signature is the same of Recv, but, instead of the status argument, it has a pointer to the request (MPI_Request) (OUT). MPI_Request is an handle that can be queryied on the status of the operation.

# MPI_Get_count

Takes:
- the status,
- the MPI data type of the message,
- a pointer to the counter of **elements** received (output).
Returns an int.

# How to check for the completion of send/receive

- `int MPI_Wait(MPI_Request *req, MPI_Status *st)` is **blocking** and it invalidates `*req` by setting it to MPI_REQUEST_NULL, regardless of the operation's success.
- `int MPI_Test(MPI_Request *req, int *flag, MPI_Status *st)` is **non-blocking** and it sets the flag to 1 if the operation was successful and invalidates `*req` by setting it to MPI_REQUEST_NULL.
- `MPI_Waitall`
- `MPI_Testall`
- `MPI_Waitany`
- `MPI_Waitall`
- `MPI_Testany`
- etc...