---
updated_at: 2025-03-11T22:44:39.723+01:00
---
Implementiamo un [[vettore]] come una lista ordinata di elementi contenuti nella [[memoria RAM]] a determinati indirizzi, con una distanza costante tra indirizzi di 4 byte (per l'architettura con word a 32 bit).

**Esempio con \[5, 10, 20\]**:

Innanzitutto riserviamo/allochiamo 3 slot di memoria RAM e inizializziamoli con 5, 10 e 20.

```
.data
	arr: .word 5, 10, 20
```

Ogni volta che scriveremo `arr`, l'assembler lo intenderà in automatico come l'indirizzo del primo elemento del vettore (0x10010000).

| Indirizzo di memoria | Valore |
| -------------------- | ------ |
| 0x10010000           | 5      |
| 0x10010004           | 10     |
| 0x10010008           | 20     |

Poi carichiamo i valori della lista dalla memoria a dei [[registri]]:

```
.text

	.globl _start

_start:

    la t1, arr        # carica l'indirizzo base di arr in t1

    # carica i valori dell'array in memoria

    lw t2, 0(t1)      # carica il valore all'indirizzo t1 + 0 in t2
    lw t3, 4(t1)      # carica il valore all'indirizzo t1 + 4 in t3
    lw t4, 8(t1)      # carica il valore all'indirizzo t1 + 8 in t4
```


| Indirizzo del registro | Valore |
| ---------------------- | ------ |
| 0x10010000             | 5      |
| 0x10010004             | 10     |
| 0x10010008             | 20     |
