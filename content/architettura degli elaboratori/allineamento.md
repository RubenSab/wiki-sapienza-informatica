---
updated_at: 2025-03-10T21:07:02.119+01:00
---
> Se in un sistema c'è il **vincolo di allineamento** di dati e istruzioni alla parola/word, allora le word devono necessariamente iniziare da indirizzi multipli della lunghezza della word (4 byte in [[RISC-V]] RV32).

Esempio: inizializzazione di un intero `i` (4 byte) e di un char `c` (4 bite)

- in una struttura (little-endian) non allineata:

| indirizzo | byte |
| --------- | ---- |
| 7         | i[3] |
| 6         | i[2] |
| 5         | i[1] |
| 4         | i[0] |
| 3         |      |
| 2         |      |
| 1         |      |
| 0         | c    |

- in una struttura (little-endian) allineata:

| indirizzo | byte |
| --------- | ---- |
| 4         | c    |
| 3         | i[3] |
| 2         | i[2] |
| i         | i[1] |
| 0         | i[0] |