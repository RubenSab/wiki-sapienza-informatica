---
updated_at: 2026-04-19T17:09:59.038+02:00
---
Le [[system call]] che terminano con un errore tipicamente ritornano il valore intero -1 e impostano la variabile globale intera `errno` con il **codice numerico dell'errore** verificatosi.

> N.B.: Una system call terminata con successo lascia invariata `errno`, quindi prima di pensare al tipo di errore bisogna controllare se l'errore si è effettivamente verificato (sys-call ha ritornato -1).

# `perror` di `stdio.h`

> `void perror(const char *prefix)` stampa su `stderr` il messaggio mnemonico di errore nel formato `prefix:messaggio_errore_mnemonico`.

- `prefix` è una stringa qualsiasi data in input;
- il messaggio mnemonico di errore è ricavato dal compilatore dalla **variabile globale `errno`**.

# `strerror` di `string.h`

> `char *strerror(int errnum)` prende in input un codice numerico di errore e restituisce il suo messaggio mnemonico.

#todo strace (pag. 22)