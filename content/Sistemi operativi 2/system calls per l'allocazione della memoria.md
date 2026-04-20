---
updated_at: 2026-04-19T17:11:21.486+02:00
---
> `malloc`, `calloc`, `realloc` sono funzioni general purpose che usano [[system call]] per la gestione della [[memoria]].

# `mmap` di `sys/mman.h`

> `void *mmap(void *addr, size_t len, int prot, int flag, int fd, off_t off)` serve per gestire il memory-mapped IO.

Permette la lettura/scrittura dal/sul buffer che risulta in lettura/scrittura dal/sul disco (senza accedere al disco).

- mappa un [[file]] su disco in un area di memoria (buffer) lunga `length` a partire da un indirizzo di memoria `addr` (se `addr=0` il sistema sceglie un indirizzo), ritornando un [[puntatore]] `void *` da castare al tipo di puntatore relativo al tipo di dato contenuto nella sezione di memoria puntata; altrimenti `MAP_FAILED` se da errore.
- `len` è il numero di byte da trasferire dal disco alla memoria,
- `prot` è il livello di protezione. Può assumere i valori:
	- `PROT_READ` se la regione di memoria può essere letta,
	- `PROT_WRITE` se la regione di memoria può essere scritta,
	- `PROT_EXEC` se la regione di memoria può essere eseguita,
	- `PROT_NONE` se la regione di memoria non può essere acceduta.
- `flag` può assumere i valori:
	- `MAP_SHARED` se le operazioni di memoria modificano il file (R/W);
	- `MAP_PRIVATE` se viene creata e modificata solo una copia privata del mapped_file.
- `fd` è il file descriptor (il file va aperto prima),
- `off` è l'offset iniziale del file.

# `brk` e `sbrk`

Cambiano la dimensione del data segment del processo.