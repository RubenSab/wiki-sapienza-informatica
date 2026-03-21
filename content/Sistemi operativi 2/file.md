---
updated_at: 2026-03-17T15:02:34.085+01:00
---
Un file possiede:

- un **utente proprietario** che è solitamente chi crea il file o la directory: definisce i [[permessi di accesso]];
- un **gruppo proprietario** che è il gruppo primario (specificato in [[etc-passwd|/etc/passwd]]) dell'utente proprietario.

> N.B.: In Linux anche le directory e i dispositivi in [[dev]] sono file. *(Vedi [[inode]])*

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
