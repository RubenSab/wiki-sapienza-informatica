---
updated_at: 2026-04-19T17:26:10.188+02:00
---
> In Linux i file sono **astrazioni** che descrivono ogni risorsa: i file su disco, le directory, i dispositivi in [[dev]], i socket e i FIFO **sono tutti file** implementati attraverso gli [[inode]].

Un file possiede:

- un **utente proprietario** che è solitamente chi crea il file o la directory: definisce i [[permessi di accesso]];
- un **gruppo proprietario** che è il gruppo primario (specificato in [[etc-passwd|/etc/passwd]]) dell'utente proprietario.

> N.B.: In Linux i nomi dei file sono *case sensitive*.

- [[file speciali]]

# Tipi di file

^90365a

Lo standard POSIX stabilisce i singoli caratteri che rappresentano i tipi di file Unix nel **formato lungo** del comando [[comandi della bash (Bourne Again shell)#^a4c080|ls]]:

- `-` se è un *file regolare*,
- `d` se è una *directory*,
- `l` se è un *symbolic link*,
- `p` se è un file speciale di un *FIFO device*,
- `b` se è un file speciale di un *block device* (dispositivo che memorizza dati),
- `c` se è un file speciale di un *character device* (dispositivo che trasferisce dati),
- `s` se è un *socket*.

# Operare sui file in C

^7c0c1a

1. Apertura del file con `open`: viene creato un file descriptor.
2. [[system call]] sul file; ad esempio `read` o `write`.
3. chiusura del file con `close` (anche se quando un processo termina chiude tutti i file aperti legati ad esso, è sempre **buona pratica** chiuderli esplicitamente).

## File descriptor

> È il **riferimento**, mantenuto da un processo, a un **file aperto**.
> È rappresentato da un piccolo intero generato sequenzialmente a partire da 0. Ogni processo al lancio ha `0` per `stdin`, `1` per `stdout` e `2` per `stderr`.

Quando si chiude un file, il suo file descriptor viene liberato e può essere riutilizzato.

> N.B.: Più file descriptor possono puntare allo stesso file.

![[Pasted image 20260419172446.png]]

### File flags

#todo pag. 38-40 SystemProgrammingAllInOne